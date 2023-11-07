# Docker Commands Reference

## Container Management

- `docker ps` - List all running containers.
- `docker ps -a` - List all containers, whether they are running or not.
- `docker ps -a -q` - List all containers id, whether they are running or not.
- `docker start container_id` - Start a container.
- `docker stop container_id` - Stop a container.

## Interactive Containers

- `docker run -it` (-i for interactive, input-free, and -t for a TTY, enabling command input on the terminal).
- `docker run -it --rm image_name` - Remove the image after exiting the container.
- `docker run -p 8080:80 image` - Publish the image with port mapping (host port / container port).
- `docker run -d` - Run in the background (detached mode).

## Container Cleanup

- `docker rm container_id` - Remove a container.
- `docker rm -f container_id` - Forcefully remove a container.
- `docker rm $(docker ps -a -q) -f` - Forcefully remove all containers.

## Named Containers

- `docker run -d --name container_name image_name` - Assign a name to a container.
- `docker exec container_name command` - Run a command inside the container.
- `docker exec -it container_id bash` - Access the bash shell inside the container.

## Bind Mounting

- `docker run -d --name nginx -p 8080:80 -v local_path:container_path image` - Use bind mounting to share a folder between your computer and the container.
- `docker run -d --name nginx -p 8080:80 --mount type=bind,source="$(pwd)",target="path_target" nginx` - Use the "bind" mount type to share a local folder with the container. You can specify the current path using "pwd."

## Docker Volumes

- `docker volume ls` - List Docker volumes.
- `docker volume create volume_name` - Create a new volume.
- `docker volume inspect volume_name` - Inspect the volume and return information.
- `docker run --name nginx -d --mount type=volume,source=my_volume,target=/app nginx` - Attach a Docker volume to a container; anything created inside the volume will be shared with all containers that use it.
- `docker volume prune` - Clean up volumes that are not in use.


## Docker images

- `docker pull image_name` - Download an image from Docker Hub.
- `docker images` - List all images.
- `docker images -a` - List all images and their dependencies.
- `docker rmi imaged_id` - Remove an image based on its ID.
- `docker build -t image_name:tag_version .` - Build a Dockerfile, setting a name, tag version, and local path.
- `docker images | grep name_to_find` - Find images with the name

## Dockerhub

- `docker login` - Log in to Docker Hub.
- `docker push image_name` -  Log in to Docker Hub.

## Network

- `docker network create -d bridge network_name` - Create a network
- `docker network ls` - List networks
- `docker network prune` - Remove unused networks
- `docker network inspect bridge` - Inspect a bridge
- `docker attach container_name` - Attach to a running container
- `docker network create --driver bridge network_name` - Create a new network
- `docker run -dit --name container_name --network network_name image_name` - Run a container on a specific network
- `docker network connect network_name container_name` - Connect a container to an existing network

## Logs
- `docker logs image_name` - See the log's of a container

## Docker Compose Commands Reference

- `docker-compose up` - Run the Docker Compose file.
- `docker-compose down` - Stop and remove containers defined in the Docker Compose file.
- `docker-compose up -d` - Run the Docker Compose in detached mode.
- `docker-compose ps` - List the containers and their status defined in the Docker Compose file.
- `docker-compose up -d --build` - Rebuild images and run the Docker Compose in detached mode.
- `docker-compose down container_name` - Stop a single container with Docker Compose
