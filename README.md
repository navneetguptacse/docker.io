<a href="https://www.docker.com/">
  <img src="https://cdn.worldvectorlogo.com/logos/docker-3.svg" alt="Description" style="width:60%; height:auto;"/>
</a>

### Pulling Images

- `docker pull imagename` or `docker image pull imagename`: Pull any Docker image from hub.docker.com.

### Running Containers

- `docker run -it <image_name>`: Run a Docker image in interactive mode.

### Executing Commands in Containers

- `docker exec <container_name> <command>`: Fetch data or results from a Docker container and return to the original terminal.
- `docker exec -it <container_name> <command>`: Fetch data or results from a Docker container, staying in that container in the original terminal.

### Listing Containers

- `docker container ls`: List all running Docker containers.
- `docker container ls -a`: List all Docker containers.

### Managing Containers

- `docker start <container_name>`: Start a running container.
- `docker stop <container_name>`: Stop a running container.

### Listing Images

- `docker images`: See all Docker images installed.
- `docker images -ls`: See the list of installed images in Docker.

### Building Images

- `docker build -t username/imagename:tag .`: Build a Docker image.

### Authentication and Pushing Images

- `docker login`: Log in to your Docker Hub account before pushing images.
- `docker tag username/imagename:tag username/imagename:tag`: Tag your image with the repository information on Docker Hub.
- `docker push username/imagename`: Push your image to Docker Hub.

## Docker Compose

Docker Compose is a tool for defining and running multi-container Docker applications. It simplifies managing complex Docker setups by allowing you to define services, networks, and volumes in a YAML file.

### `docker-compose.yml` Example

```yaml
# this file is a helper to run cal.com locally
# starts a postgres instance on port 5450 to use as a local db

version: "3.6"
services:
  postgres:
    image: postgres:13
    ports:
      - "5450:5432" # expose pg on port 5450 to not collide with pg from elsewhere
    restart: always
    volumes:
      - db_data:/var/lib/postgresql/data
    environment:
      POSTGRES_DB: "cal-saml"
      POSTGRES_PASSWORD: ""
      POSTGRES_HOST_AUTH_METHOD: trust
    healthcheck:
      test: ["CMD-SHELL", "pg_isready"]
      interval: 10s
      timeout: 5s
      retries: 5
  postgres_is_ready:
    image: postgres
    depends_on:
      postgres:
        condition: service_healthy
volumes:
  db_data:
```

### Docker Compose Commands

`docker compose up`: Spin up all configurations defined in `docker-compose.yml`.
Press **Ctrl + C** to stop all containers or use `docker container stop`.
`docker compose down`: Remove everything from Docker containers.
`docker compose up -d`: Run in detached mode, meaning it runs in the background.

### Docker Cheatsheet

[here >>>](https://red-tabina-69.tiiny.site/)

Feel free to modify and expand upon this README file according to your project's specific needs.
"# .docker-git.md"
