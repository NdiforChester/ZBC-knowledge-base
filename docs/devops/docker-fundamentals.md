# Docker Fundamentals

Docker is a platform for packaging applications and their dependencies into containers. A container runs the same way across different environments, which helps solve the common problem: "It works on my machine, but not on the server."

## 1. What a Container Is

A container is an isolated runtime environment for an application.

A container usually includes:

- Application code.
- Runtime.
- Libraries.
- System dependencies.
- Configuration needed to start the application.

Containers share the host operating system kernel, which makes them lighter than full virtual machines.

## 2. Docker Images and Containers

| Concept | Meaning |
| --- | --- |
| Image | A read-only template used to create containers |
| Container | A running instance of an image |
| Dockerfile | Instructions for building an image |
| Registry | A place where images are stored |

Example:

```bash
docker run nginx
```

This command downloads the `nginx` image if needed and starts a container from it.

## 3. Why Docker Matters

Docker helps teams:

- Package applications consistently.
- Run local development environments.
- Build repeatable CI/CD pipelines.
- Deploy applications to servers or Kubernetes.
- Separate application dependencies from the host machine.

## 4. Common Commands

List running containers:

```bash
docker ps
```

List all containers:

```bash
docker ps -a
```

List images:

```bash
docker images
```

Run a container:

```bash
docker run -d -p 8080:80 nginx
```

Stop a container:

```bash
docker stop <container-id>
```

Remove a container:

```bash
docker rm <container-id>
```

Remove an image:

```bash
docker rmi <image-id>
```

## 5. Dockerfile Basics

Example Dockerfile:

```Dockerfile
FROM nginx:alpine
COPY ./site /usr/share/nginx/html
EXPOSE 80
```

Build the image:

```bash
docker build -t zbc-site:1.0 .
```

Run the image:

```bash
docker run -d -p 8080:80 zbc-site:1.0
```

## 6. Ports and Volumes

Port mapping connects host ports to container ports:

```bash
docker run -p 8080:80 nginx
```

This maps port `8080` on your machine to port `80` inside the container.

Volumes persist data outside the container lifecycle:

```bash
docker volume create app-data
docker run -v app-data:/data nginx
```

## 7. Beginner to Intermediate Practice Path

1. Run an `nginx` container.
2. Map a host port to the container.
3. Build a custom image from a Dockerfile.
4. Inspect logs with `docker logs`.
5. Use a volume for persistent data.
6. Push an image to a registry.

## 8. Common Mistakes to Avoid

- Putting secrets in Dockerfiles.
- Running containers as root when not required.
- Building huge images with unnecessary files.
- Forgetting to tag images clearly.
- Treating containers as permanent servers instead of replaceable units.
