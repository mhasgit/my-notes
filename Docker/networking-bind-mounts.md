# Docker Notes

## Volumes

- **Purpose**: Volumes are a state that persists data outside of Docker containers and can be shared across multiple containers that are running.
- **Usage**:
  - Volumes are meant to retain data even when containers are deleted.
  - Docker volumes can either be managed by Docker itself or manually by users.
  - **Commands**: 
    - `docker volume create <volume-name>`: Creates a new volume.
    - `docker run -v <volume-name>:/path/in/container <image>`: Mounts a volume into a container.
  - **Docker-managed volumes**:
    - Command: `docker run -v /var/www <image>` mounts a Docker-managed volume.
    - Inspect command: `docker inspect <container>` shows the volume mount details.
  - **Customized volumes**:
    - Command example: `docker run -v $(pwd)/local/path:/container/path <image>` to mount a user-managed volume.

## Networking with Docker

- **Purpose**: Docker networking allows containers to communicate with each other, either in isolation or within a custom network.
- **Common Network Types**:
  - **Bridge Network**: The default network for container-to-container communication.
- **Commands**:
  - `docker network create --driver=bridge <network-name>`: Creates a new bridge network.
  - `docker run --network=<network-name> --name=<container-name> <image>`: Connects a container to a specified network.
  - **Example for MongoDB**: 
    - `docker run -d --network=app-net --name=db mongo`: Runs MongoDB in a specific network.
    - `docker run -p 8080:8080 --network=app-net --env MONGO_CONNECTION_STRING=mongodb://db <app-image>`: Connects an application to the MongoDB container using a network.

## Docker Compose

- **Purpose**: Useful for defining and managing multi-container Docker applications in local development.
- **Use Case**: Preferred for local development with multiple containers; for larger deployments, Kubernetes is recommended.
- **Commands**:
  - `docker-compose build`: Builds all defined images.
  - `docker-compose up`: Starts all services defined in the `docker-compose.yml` file.
  - `docker-compose down`: Stops and removes all services.

## Docker Scout

- **Purpose**: Docker Scout scans containers for vulnerabilities and identifies components that may be problematic.
- **Usage**:
  - `docker scout <command> <container-name>`: Scans the specified container.
  - **Example**:
    - `docker scout quickview <container-name>`: Provides a quick view of vulnerabilities.
    - `docker scout overview <container-name>`: Gives an overview of common vulnerabilities.

## Bind Mounts

- **Purpose**: Bind mounts are used to share local files or directories from the host with Docker containers, allowing direct access to host files.
- **Use Case**: Ideal for development environments where you don’t want to rebuild the container each time changes are made to files.
- **Commands**:
  - `docker run --mount type=bind,source="$(pwd)",target=/usr/share/nginx/html <image>`: Mounts the current directory into the container.
- **Characteristics**:
  - Anything saved within the bind mount is also saved directly to the host computer.
  - Bind mounts provide more direct control over files compared to Docker volumes but can be less secure if not handled carefully.
