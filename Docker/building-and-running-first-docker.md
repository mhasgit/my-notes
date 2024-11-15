# Building and Running Your First Docker App

## Dockerfile and .dockerignore

- **Dockerfile**:
  - A `Dockerfile` is a script that contains a series of commands to create a Docker image.
  - Example structure of a `Dockerfile`:
    ```dockerfile
    FROM node:14
    WORKDIR /app
    COPY . .
    RUN npm install
    CMD ["node", "app.js"]
    ```
  - **Explanation**:
    - `FROM`: Specifies the base image to use (e.g., `node:14`).
    - `WORKDIR`: Sets the working directory inside the container.
    - `COPY`: Copies files from the host to the container.
    - `RUN`: Runs a command, such as installing dependencies.
    - `CMD`: Specifies the command to run when the container starts.

- **.dockerignore**:
  - The `.dockerignore` file specifies files and directories to ignore when building a Docker image (similar to `.gitignore` in Git).
  - Helps to reduce the image size by excluding unnecessary files.

---

## Building Docker Images

- **Build an Image**:
  - Command:
    ```bash
    docker build -t <image_name> .
    ```
  - **Options**:
    - `-t`: Specifies the tag or name of the image.
    - `.`: The current directory as the build context.
  - **Example**:
    ```bash
    docker build -t nodeapp .
    ```

- **Building with Custom Dockerfile and Tags**:
  - Command:
    ```bash
    docker build -t <repository>/<name>:<tag> -f <Dockerfile_path> .
    ```
  - Example:
    ```bash
    docker build -t myrepo/nodeapp:1.0 -f node.Dockerfile .
    ```
  - This command builds an image with a specific repository name and tag.

- **Image Versioning**:
  - It's common to tag images with a version (e.g., `nodeapp:1.0`) to track different versions of the application.

---

## Managing Docker Images

- **Listing Images**:
  - Command:
    ```bash
    docker images
    ```
  - Displays all images available on the host.

- **Removing Images**:
  - Command:
    ```bash
    docker rmi <image_id>
    ```
  - Removes the specified image by ID. Use caution, as this will delete the image permanently.

---

## Deploying an Image to a Docker Registry

- **Push an Image**:
  - Command:
    ```bash
    docker push <username>/<image_name>:<tag>
    ```
  - This command uploads the image to a Docker registry (e.g., Docker Hub, Amazon ECR, Azure Container Registry).

- **Login to Docker Hub**:
  - Command:
    ```bash
    docker login
    ```
  - Prompts for Docker Hub credentials. Alternatively, you can use an access token for authentication.

> **Note**: Images in Docker Hub can be public or private, depending on your preference.

---

# Running Containers from Images

## Running a Docker Container

- **Basic Run Command**:
  - Command:
    ```bash
    docker run <image_name>
    ```
  - Runs a container based on the specified image.

- **Running with Port Mapping**:
  - Command:
    ```bash
    docker run -p <host_port>:<container_port> <image_name>
    ```
  - Example:
    ```bash
    docker run -p 8080:80 nginx
    ```
  - **Explanation**:
    - `-p 8080:80`: Maps port 8080 on the host to port 80 in the container, allowing access to the container's web service via port 8080.

- **Running in Detached Mode**:
  - Command:
    ```bash
    docker run -d <image_name>
    ```
  - Runs the container in the background (detached mode) without displaying logs in the terminal.

- **Viewing Container Logs**:
  - Command:
    ```bash
    docker logs <container_id>
    ```
  - Shows logs for the specified container.

---

# Docker Volumes

## Using Volumes for Data Persistence

- **Overview**:
  - Volumes are used to store data persistently outside of the container's filesystem.
  - This allows data to persist even if the container is removed.

- **Creating and Mounting Volumes**:
  - Command:
    ```bash
    docker run -p <host_port>:<container_port> -v <host_path>:<container_path> <image_name>
    ```
  - Example:
    ```bash
    docker run -p 8080:80 -v /var/www/logs:/app/logs nginx
    ```
  - **Explanation**:
    - `-v /var/www/logs:/app/logs`: Mounts the host directory `/var/www/logs` to `/app/logs` in the container, enabling persistent storage of logs.

- **Using Environment Variables for Paths**:
  - Command:
    ```bash
    docker run -p <host_port>:<container_port> -v $(pwd):/app/logs <image_name>
    ```
  - On Windows PowerShell:
    ```powershell
    docker run -p <host_port>:<container_port> -v ${PWD}:/app/logs <image_name>
    ```
  - **Explanation**:
    - `$(pwd)`: Uses the current directory path (on macOS/Linux) for mounting. `${PWD}` is used on Windows PowerShell.

> **Note**: Volumes are the preferred way to store persistent data for Docker containers, as they offer more flexibility than bind mounts and can be managed independently of the container lifecycle.

---

# Additional Docker Tips and Best Practices

- **Immutability of Images**:
  - Docker images are immutable, meaning they cannot be changed once built. Any changes require a new build and version.

- **Keeping Docker Images Small**:
  - Use smaller base images, like `alpine`, to reduce image size.
  - Use multi-stage builds to minimize final image size by only including essential files.

- **Using Docker Compose for Multi-Container Applications**:
  - **Docker Compose** is a tool that allows defining and running multi-container Docker applications using a `docker-compose.yml` file.
  - Example `docker-compose.yml`:
    ```yaml
    version: '3'
    services:
      web:
        image: nginx
        ports:
          - "8080:80"
      app:
        image: nodeapp
        volumes:
          - ./app:/app
    ```
  - **Command**:
    ```bash
    docker-compose up
    ```
  - **Explanation**:
    - `docker-compose up` brings up all services defined in the file, making it easier to manage complex setups.

- **Monitoring and Debugging**:
  - Use `docker stats` to monitor container resource usage.
  - Use `docker exec -it <container_id> bash` to open an interactive terminal in a running container for debugging.

- **Cleaning Up Unused Resources**:
  - **Remove Stopped Containers**:
    ```bash
    docker container prune
    ```
  - **Remove Unused Images**:
    ```bash
    docker image prune
    ```
  - **Remove All Unused Volumes**:
    ```bash
    docker volume prune
    ```
  - These commands help keep the Docker environment clean and free of unused resources.

