# Docker for Web Developers

## Volume Management in Docker

### Types of Volumes
- **Managed by Docker**: Docker automatically handles the volume storage path.
- **Managed by User**: User specifies the path on the host for the volume.

### Using Docker Managed Volumes
- **Run a Container with Docker Managed Volume**:
    ```bash
    docker run -p 8080:3000 -v /var/www <image_name>
    ```
- **Inspecting Volume Information**:
    ```bash
    docker inspect <container_name>
    ```
    - In the `Mounts` section, you can view details like:
      - `"Source"`: Path managed by Docker (e.g., `/var/lib/docker/volumes/`).
      - `"Destination"`: Path within the container (e.g., `/var/www`).

### Using Customized Volumes
- **Run a Container with Custom Volume**:
    ```bash
    docker run -p 8080:3000 -v $(pwd):/var/www <image_name>
    ```
  - **Explanation**:
    - `$(pwd)`: Binds the current working directory on the host to `/var/www` in the container.
    - This allows you to control the host storage path and organize data outside of Docker's management.

---

## Removing Volumes

- **Removing Volume with Container**:
    ```bash
    docker rm -v <container_name>
    ```
  - **Note**: This only works if the container is stopped. It removes the volume associated with the specified container.

- **Removing Custom Volumes**:
    - Use `docker volume rm <volume_name>` to manually remove custom volumes since they are not automatically deleted with containers.

- **Cleaning Up All Unused Volumes**:
    ```bash
    docker system prune --volumes
    ```
  - Removes all unused volumes to free up space.

---

# Building Custom Images

### Basic Custom Image Build
- **Building an Image with a Custom Tag**:
    ```bash
    docker build -t <your_username>/<image_name> .
    ```
  - **Explanation**:
    - `-t`: Tags the image with a name.
    - This command reads instructions from the `Dockerfile` in the current directory to build the image.

---

# Multi-Stage Dockerfile

### Purpose of Multi-Stage Builds
- Multi-stage builds allow for:
  - **Separation of Build and Production Stages**: Helps reduce image size by only including the final application code, not build dependencies.
  - **Efficient Image Creation**: Compiling code in one stage and using only the necessary output in the final image.

### Example Workflow with Multi-Stage Dockerfile
1. **Stage 1**: Build the application.
    - This stage may use an SDK to compile the code and create an intermediate image.
2. **Stage 2**: Copy only the compiled code or required files into a final, minimal production image.

### Example of Multi-Stage Dockerfile
```dockerfile
# Stage 1: Build
FROM node:14 AS builder
WORKDIR /app
COPY . .
RUN npm install && npm run build

# Stage 2: Production
FROM nginx:alpine
COPY --from=builder /app/dist /usr/share/nginx/html

**Explanation**: The build stage creates the compiled output, and the production stage only includes this output, making the final image smaller and more secure.

**Note**: Multi-stage builds are particularly useful for applications with heavy dependencies during build but require a lean production environment.
