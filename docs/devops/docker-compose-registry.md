# Docker Compose and Registries

Docker Compose manages multi-container applications with a YAML file. A Docker registry stores and distributes container images.

Together, Compose and registries help teams run complete systems locally, share images, and move applications through CI/CD pipelines.

## 1. What Docker Compose Does

Docker runs one container at a time. Docker Compose describes multiple containers and starts them together.

Example application:

- Frontend container.
- Backend API container.
- Database container.
- Cache container.

Instead of running many `docker run` commands, you define services in `compose.yaml`.

## 2. Basic Compose File

```yaml
services:
  web:
    image: nginx:alpine
    ports:
      - "8080:80"

  database:
    image: mysql:8
    environment:
      MYSQL_ROOT_PASSWORD: example
      MYSQL_DATABASE: appdb
```

Start services:

```bash
docker compose up
```

Start in the background:

```bash
docker compose up -d
```

Stop and remove services:

```bash
docker compose down
```

## 3. Service Dependencies

Use `depends_on` when one service should start before another:

```yaml
services:
  api:
    build: .
    depends_on:
      - database

  database:
    image: postgres:16
```

`depends_on` controls startup order. It does not guarantee the database is ready to accept connections. Applications should still retry connections.

## 4. Common Docker Compose Commands

```bash
docker compose ps
docker compose logs
docker compose logs -f api
docker compose exec api sh
docker compose build
docker compose restart
docker compose down --volumes
```

Use `down --volumes` carefully because it removes named volumes and can delete local database data.

## 5. Environment Variables

Do not commit secrets into Compose files. Use environment variables or local `.env` files.

Example:

```yaml
services:
  api:
    image: my-api:1.0
    environment:
      DB_HOST: database
      DB_USER: ${DB_USER}
      DB_PASSWORD: ${DB_PASSWORD}
```

Example `.env` file:

```text
DB_USER=appuser
DB_PASSWORD=change-me-locally
```

If `.env` contains secrets, add it to `.gitignore`.

## 6. What a Docker Registry Is

A registry stores Docker images so they can be pulled by other machines or deployment platforms.

Common registry types:

| Type | Example |
| --- | --- |
| Public registry | Docker Hub |
| Private cloud registry | Amazon ECR, GitHub Container Registry |
| Self-hosted registry | Private registry server |

## 7. Amazon ECR

Amazon Elastic Container Registry (ECR) is AWS's managed private container registry.

Basic ECR workflow:

1. Create an ECR repository.
2. Authenticate Docker to ECR.
3. Build an image.
4. Tag the image with the ECR repository URL.
5. Push the image.
6. Pull it from ECS, EKS, or another deployment target.

Example commands:

```bash
aws ecr get-login-password --region eu-north-1 \
  | docker login --username AWS --password-stdin 123456789012.dkr.ecr.eu-north-1.amazonaws.com

docker build -t nginx-demo:1.0 .
docker tag nginx-demo:1.0 123456789012.dkr.ecr.eu-north-1.amazonaws.com/nginx-demo:1.0
docker push 123456789012.dkr.ecr.eu-north-1.amazonaws.com/nginx-demo:1.0
```

## 8. Best Practices

- Keep Compose files readable and committed with application code.
- Keep secrets out of Git.
- Use named volumes for data that must persist.
- Use image tags such as `1.0.0` instead of only `latest`.
- Scan images for vulnerabilities in CI/CD.
- Remove unused local containers and images periodically.

## 9. Practice Tasks

1. Create a Compose file with a web server and database.
2. Start it with `docker compose up -d`.
3. Inspect logs.
4. Stop it with `docker compose down`.
5. Build and tag a custom image.
6. Explain the difference between Docker Hub and Amazon ECR.
