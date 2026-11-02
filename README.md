# Containerized Django Application (Docker 2026)

This repository contains the complete setup for containerizing and running a Django web application using Docker and Docker Compose.

---

## Prerequisites

- [Docker Desktop](https://www.docker.com/products/docker-desktop) installed on Windows/Mac or Docker Engine on Linux.
- Docker Hub account (for pushing/pulling images).

---

## Developer Workflow (Building & Publishing Image)

### 1. Build and Test Locally
Build the Docker image locally:
```bash
docker build -t my-django-app:latest .
```

Alternatively, run the project locally using Compose:
```bash
docker-compose up -d --build
```
Access the application at `http://localhost:8000`.

---

### 2. Push Image to Docker Hub

1. Log in to your Docker Hub account:
   ```bash
   docker login
   ```

2. Tag the built image with your Docker Hub username:
   ```bash
   docker tag my-django-app:latest yourusername/django-app:latest
   ```

3. Push the image to Docker Hub:
   ```bash
   docker push yourusername/django-app:latest
   ```

---

## Client / Deployment Workflow (Running pulled Image)

To run the application on any other machine without needing the source code:

1. Navigate to the client directory:
   ```bash
   cd for_client
   ```

2. Run the application using Docker Compose:
   ```bash
   docker-compose up -d
   ```

3. (First Time Only) Create an administrative superuser:
   ```bash
   docker-compose exec web python manage.py createsuperuser
   ```

4. View running logs:
   ```bash
   docker-compose logs -f web
   ```

5. Stop the container environment:
   ```bash
   docker-compose down
   ```
