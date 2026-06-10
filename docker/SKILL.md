---
name: docker
description: "Containerize applications with Docker and write Dockerfiles. Use when creating container images, setting up Docker Compose, or managing container orchestration."
---

# Docker Skill

Build and manage Docker containers, images, and Compose files for consistent deployment.

## When to Use

Use this skill when the user wants to:
- Write Dockerfiles for containerization
- Create docker-compose.yml files
- Optimize Docker image size
- Multi-stage builds
- Docker networking and volumes
- Docker secrets and configs
- Container orchestration basics

## Dockerfile Best Practices

- **Use official base images**: Prefer lightweight, minimal images like `alpine` or `distroless` to reduce attack surface and image size.
- **Multi-stage builds**: Separate build environments from runtime environments to keep production images small and secure.
- **Leverage layer caching**: Order instructions so that frequently changed files (like source code) are copied *after* rarely changed ones (like dependency files).
- **Minimize layers**: Combine related commands (e.g., `RUN apt-get update && apt-get install ...`) to reduce the number of image layers.
- **Clean up**: Remove temporary files, caches, and unnecessary packages within the same `RUN` command.
- **Run as non-root user**: Never run your application as `root` inside a container to mitigate potential container breakout attacks.

## Docker Compose

Define multi-container environments including services, networks, and volumes:

```yaml
version: '3.8'
services:
  web:
    build: .
    ports:
      - "8000:8000"
    environment:
      - DATABASE_URL=postgres://user:password@db:5432/mydb
    depends_on:
      - db

  db:
    image: postgres:15-alpine
    environment:
      POSTGRES_USER: user
      POSTGRES_PASSWORD: password
      POSTGRES_DB: mydb
    volumes:
      - postgres_data:/var/lib/postgresql/data

volumes:
  postgres_data:
```

## Docker Networking & Volumes

- **Networking**: Use custom bridge networks to allow containers to communicate by service name rather than IP address.
- **Volumes**: Use named volumes for persistent data that should survive container restarts and removals.
- **Bind Mounts**: Use bind mounts during development to sync local source code into the container in real-time.

## Common Pitfalls

- **Storing Secrets in Images**: Hardcoding API keys or credentials in a Dockerfile. Always use environment variables or Docker Secrets.
- **Large Image Sizes**: Using full-featured base images (e.g., `ubuntu` or `node:latest`) without cleanup, leading to slow pulls and large attack surfaces.
- **Running as Root**: Leaving the default `root` user active, which increases security risks if the container is compromised.
- **Not using `.dockerignore`**: Including unnecessary files like `.git`, `node_modules`, or local logs in your image, increasing size and potentially leaking sensitive info.

## Deliverables

- Optimized Dockerfile
- docker-compose.yml (if needed)
- .dockerignore file
- Container runtime documentation

## Quality Checklist

- [ ] Image size is minimized using lightweight base images and multi-stage builds.
- [ ] Security best practices followed (non-root user, no secrets in image).
- [ ] Ports and volumes are properly mapped and used for persistence.
- [ ] Environment variables are used for configuration.
- [ ] Network isolation is configured via custom networks.
- [ ] `.dockerignore` is present and correctly configured.
