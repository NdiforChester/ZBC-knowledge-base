# Docker Fundamentals

Docker is an open-source platform used to develop, package, ship, and run applications inside lightweight environments called **containers**.

Containers allow applications to run consistently across different environments such as:
- Developer laptops
- Test environments
- Production servers
- Cloud platforms

---

# What is Docker?

Docker is a containerization platform that helps developers package applications together with:
- Source code
- Dependencies
- Libraries
- Configuration files

This ensures the application works the same way everywhere.

---

# What is Containerization?

Containerization is the process of packaging an application and its dependencies into a single isolated unit called a **container**.

Containers are:
- Lightweight
- Portable
- Fast
- Consistent

Unlike virtual machines, containers share the host operating system kernel, making them more efficient.

---

# Benefits of Docker

## Portability
Applications run the same in development, testing, and production.

## Consistency
Eliminates the common problem:
> "It works on my machine."

## Scalability
Containers can easily scale up or down.

## Isolation
Applications run independently without interfering with each other.

## Fast Deployment
Containers start quickly compared to virtual machines.

---

# Docker Architecture

Docker uses a client-server architecture.

## Docker Client
The command-line interface used to interact with Docker.

Example:
```bash
docker ps
```

---

## Docker Daemon
The background service responsible for:
- Building images
- Running containers
- Managing Docker objects

---

## Docker Registry
A repository used to store Docker images.

Example:
- Docker Hub

Official website:
https://hub.docker.com/

---

# Docker Components

# Docker Image

A Docker image is a read-only template used to create containers.

It contains:
- Application code
- Dependencies
- Libraries
- Environment settings

Example:
```bash
docker pull nginx
```

---

# Docker Container

A container is a running instance of a Docker image.

Example:
```bash
docker run nginx
```

---

# Dockerfile

A Dockerfile is a text file containing instructions used to build Docker images.

Example:
```dockerfile
FROM ubuntu:latest

RUN apt update && apt install -y nginx

CMD ["nginx", "-g", "daemon off;"]
```

---

# Docker Volume

Docker volumes are used for persistent data storage.

They allow data to remain available even if a container is removed.

Example:
```bash
docker volume create myvolume
```

---

# Docker Network

Docker networking allows containers to communicate with:
- Other containers
- Host systems
- External networks

Example:
```bash
docker network ls
```

---

# Important Docker Commands

# Check Docker Version

```bash
docker --version
```

---

# Pull an Image

```bash
docker pull ubuntu
```

---

# List Images

```bash
docker images
```

---

# Run a Container

```bash
docker run ubuntu
```

---

# Run Container in Background

```bash
docker run -d nginx
```

---

# List Running Containers

```bash
docker ps
```

---

# List All Containers

```bash
docker ps -a
```

---

# Stop a Container

```bash
docker stop <container-id>
```

---

# Remove a Container

```bash
docker rm <container-id>
```

---

# Remove an Image

```bash
docker rmi <image-id>
```

---

# Build Docker Image

```bash
docker build -t myimage .
```

---

# To clean your machine

```bash
docker system prune -a
```
⚠ Warning:
docker system prune -a removes ALL unused images, containers, and networks.
Use with caution.
---

# Docker Lifecycle

The basic Docker workflow is:

1. Create a Dockerfile
2. Build the Docker image
3. Run the container
4. Push the image to Docker Hub (optional)

---

# Difference Between Docker Images and Containers

| Docker Image | Docker Container |
|---|---|
| Blueprint/template | Running instance |
| Read-only | Read-write |
| Cannot run by itself | Executes the application |
| Used to create containers | Created from images |

---

# Docker vs Virtual Machines

| Docker Containers | Virtual Machines |
|---|---|
| Lightweight | Heavy |
| Share host OS kernel | Have full guest OS |
| Fast startup | Slower startup |
| Lower resource usage | Higher resource usage |

---

# Common Docker Use Cases

Docker is commonly used for:

- Application deployment
- Microservices
- CI/CD pipelines
- Development environments
- Cloud-native applications
- Testing environments

---

# Example Docker Workflow

## Step 1 — Create a Dockerfile

```dockerfile
FROM nginx
```

---

## Step 2 — Build Image

```bash
docker build -t my-nginx .
```

---

## Step 3 — Run Container

```bash
docker run -d -p 8080:80 my-nginx
```

---

# Docker Hub

Docker Hub is the default public registry for Docker images.

Official website:
https://hub.docker.com/

Developers can:
- Upload images
- Share images
- Download official images

---

# Best Practices

- Keep images small
- Use official base images
- Avoid storing secrets inside images
- Use `.dockerignore`
- Tag images properly
- Remove unused containers and images

---

# Basic Troubleshooting Commands

## View Running Containers

```bash
docker ps
```

---

## View Container Logs

```bash
docker logs <container-id>
```

---

## Access Container Shell

```bash
docker exec -it <container-id> bash
```

---

## Inspect Docker Objects

```bash
docker inspect <container-id>
```

---

# Real-World Example

A web application may use:
- Frontend container
- Backend container
- Database container

Docker allows all services to run consistently together.

---

# Useful Resources

## Official Docker Documentation
https://docs.docker.com/

---

## Docker Hub
https://hub.docker.com/

---

## Play with Docker
https://labs.play-with-docker.com/

---

# Summary

Docker is a powerful containerization platform that simplifies:
- Application deployment
- Environment consistency
- Scalability
- Collaboration

Understanding Docker fundamentals is essential for:
- DevOps
- Cloud Computing
- CI/CD
- Software Development
- Platform Engineering

