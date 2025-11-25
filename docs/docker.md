# Docker Basics

This guide introduces Docker, a platform for developing, shipping, and running applications in containers.

---

## Table of Contents

1. [What is Docker?](#what-is-docker)
2. [Key Concepts](#key-concepts)
3. [Installation](#installation)
4. [Basic Commands](#basic-commands)
5. [Working with Images](#working-with-images)
6. [Working with Containers](#working-with-containers)
7. [Dockerfile Basics](#dockerfile-basics)
8. [Docker Compose](#docker-compose)
9. [Volumes and Persistence](#volumes-and-persistence)
10. [Networking](#networking)
11. [Best Practices](#best-practices)

---

## What is Docker?

Docker is a platform that uses containerization to package applications and their dependencies into standardized units called containers.

**Benefits of Docker:**

- **Consistency:** Same environment across development, testing, and production
- **Isolation:** Applications run independently without conflicts
- **Portability:** Containers run on any system with Docker installed
- **Efficiency:** Lightweight compared to virtual machines
- **Scalability:** Easy to scale applications horizontally

---

## Key Concepts

| Term | Description |
|------|-------------|
| **Image** | Read-only template containing application and dependencies |
| **Container** | Running instance of an image |
| **Dockerfile** | Text file with instructions to build an image |
| **Registry** | Storage for Docker images (e.g., Docker Hub) |
| **Volume** | Persistent storage for container data |
| **Network** | Communication between containers |

---

## Installation

### Windows

1. Download [Docker Desktop](https://www.docker.com/products/docker-desktop)
2. Run installer and follow prompts
3. Enable WSL 2 if prompted
4. Start Docker Desktop

### Verify Installation

```bash
docker --version
docker run hello-world
```

---

## Basic Commands

### System Commands

```bash
# Check Docker version
docker --version

# View system info
docker info

# View disk usage
docker system df

# Clean up unused resources
docker system prune
```

---

## Working with Images

### Pulling Images

```bash
# Pull image from Docker Hub
docker pull nginx

# Pull specific version
docker pull nginx:1.25

# Pull from specific registry
docker pull ghcr.io/owner/image:tag
```

### Listing Images

```bash
# List all images
docker images

# List with more details
docker images -a
```

### Removing Images

```bash
# Remove specific image
docker rmi nginx

# Remove by image ID
docker rmi abc123

# Remove all unused images
docker image prune
```

---

## Working with Containers

### Running Containers

```bash
# Run container (foreground)
docker run nginx

# Run in background (detached)
docker run -d nginx

# Run with custom name
docker run -d --name my-nginx nginx

# Run with port mapping
docker run -d -p 8080:80 nginx

# Run with environment variables
docker run -d -e MY_VAR=value nginx

# Run interactively
docker run -it ubuntu bash
```

### Managing Containers

```bash
# List running containers
docker ps

# List all containers
docker ps -a

# Stop container
docker stop my-nginx

# Start stopped container
docker start my-nginx

# Restart container
docker restart my-nginx

# Remove container
docker rm my-nginx

# Remove running container (force)
docker rm -f my-nginx

# View container logs
docker logs my-nginx

# Follow logs
docker logs -f my-nginx

# Execute command in running container
docker exec -it my-nginx bash
```

---

## Dockerfile Basics

A Dockerfile defines how to build an image.

### Example Dockerfile

```dockerfile
# Base image
FROM node:18-alpine

# Set working directory
WORKDIR /app

# Copy package files
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy application code
COPY . .

# Expose port
EXPOSE 3000

# Start command
CMD ["npm", "start"]
```

### Common Instructions

| Instruction | Purpose |
|-------------|---------|
| `FROM` | Base image |
| `WORKDIR` | Set working directory |
| `COPY` | Copy files from host |
| `ADD` | Copy files (supports URLs) |
| `RUN` | Execute command during build |
| `ENV` | Set environment variable |
| `EXPOSE` | Document exposed ports |
| `CMD` | Default command to run |
| `ENTRYPOINT` | Configure container as executable |

### Building Images

```bash
# Build image
docker build -t my-app .

# Build with specific Dockerfile
docker build -f Dockerfile.dev -t my-app:dev .

# Build with build arguments
docker build --build-arg VERSION=1.0 -t my-app .
```

---

## Docker Compose

Docker Compose manages multi-container applications using a YAML file.

### Example docker-compose.yml

```yaml
version: '3.8'

services:
  web:
    build: .
    ports:
      - "3000:3000"
    environment:
      - NODE_ENV=development
    volumes:
      - .:/app
    depends_on:
      - db

  db:
    image: postgres:15
    environment:
      POSTGRES_USER: user
      POSTGRES_PASSWORD: password
      POSTGRES_DB: myapp
    volumes:
      - postgres_data:/var/lib/postgresql/data

volumes:
  postgres_data:
```

### Compose Commands

```bash
# Start services
docker compose up

# Start in background
docker compose up -d

# Stop services
docker compose down

# View logs
docker compose logs

# Rebuild images
docker compose build

# Scale services
docker compose up -d --scale web=3
```

---

## Volumes and Persistence

Volumes persist data beyond container lifecycle.

### Volume Types

```bash
# Named volume
docker run -v mydata:/app/data nginx

# Bind mount (host directory)
docker run -v /host/path:/container/path nginx

# Anonymous volume
docker run -v /app/data nginx
```

### Managing Volumes

```bash
# Create volume
docker volume create mydata

# List volumes
docker volume ls

# Inspect volume
docker volume inspect mydata

# Remove volume
docker volume rm mydata

# Remove unused volumes
docker volume prune
```

---

## Networking

Docker provides networking for container communication.

### Network Types

| Type | Description |
|------|-------------|
| **bridge** | Default, containers on same bridge can communicate |
| **host** | Container shares host's network |
| **none** | No networking |
| **overlay** | Multi-host networking for swarm |

### Network Commands

```bash
# Create network
docker network create mynetwork

# List networks
docker network ls

# Connect container to network
docker network connect mynetwork my-container

# Run container on specific network
docker run -d --network mynetwork --name web nginx

# Inspect network
docker network inspect mynetwork
```

---

## Best Practices

### Dockerfile Best Practices

1. **Use specific base image tags:** `FROM node:18-alpine` instead of `FROM node`
2. **Minimize layers:** Combine RUN commands with `&&`
3. **Order matters:** Put frequently changing steps last for better caching
4. **Use .dockerignore:** Exclude unnecessary files
5. **Don't run as root:** Create non-root user

### Example .dockerignore

```text
node_modules
.git
.gitignore
*.md
.env
.DS_Store
```

### Security Best Practices

1. Scan images for vulnerabilities
2. Use official base images
3. Keep images updated
4. Don't store secrets in images
5. Use multi-stage builds for smaller images

### Multi-Stage Build Example

```dockerfile
# Build stage
FROM node:18-alpine AS builder
WORKDIR /app
COPY package*.json ./
RUN npm ci
COPY . .
RUN npm run build

# Production stage
FROM node:18-alpine
WORKDIR /app
COPY --from=builder /app/dist ./dist
COPY --from=builder /app/node_modules ./node_modules
CMD ["node", "dist/index.js"]
```

---

## Further Resources

- **Official Documentation:** [docs.docker.com](https://docs.docker.com/)
- **Docker Hub:** [hub.docker.com](https://hub.docker.com/)
- **Docker Compose Docs:** [docs.docker.com/compose](https://docs.docker.com/compose/)
- **Dockerfile Reference:** [docs.docker.com/engine/reference/builder](https://docs.docker.com/engine/reference/builder/)
- **Docker Best Practices:** [docs.docker.com/develop/develop-images/dockerfile_best-practices](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/)

---

**Happy containerizing!** 🐳
