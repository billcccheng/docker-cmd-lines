# This is a place where I put things I learned about Docker

## Good Tutorials for Docker beginners

1. [CTO of Docker giving a great introduction on Docker](https://www.youtube.com/watch?v=Q5POuMHxW-0)
2. [A very good tutorial for first time Docker users](https://training.docker.com/introduction-to-docker)

## Some useful command line for Docker
```
# Get Docker running
sudo systemctl start docker

# Docker build
docker build -t <image-name>:<tag>

# Run Docker with shell
docker run -it <image-name>:<tag> <cmd>

# Run Docker with cmd
docker run -it <image-name>:<tag> <cmd>

# Run Docker with only the Docker port exposed (Docker will randomly map a host port to this port)
docker run -it -p <docker-port-#> <image-name:tag>

# Run Docker detached and with port mapping
docker run -d -p <host-port-#>:<docker-port-#> <image-name:tag>


### Container Related ###

# List Running Container
docker ps

# List All Container(Running or exited)
docker ps -a

# Detach Container without exiting shell
<ctrl> + p + q

# Attach back to running Container with bash
docker exec -it <container-uid> /bin/bash

# Commit Docker Containers
docker commit <container-uid> <name:tag>

# Docker kill Containers
docker kill <container-uid>

# Remove exited Containers
docker rm $(docker ps -q -f status=exited)

# Remove all Containers
docker rm $(docker ps -a -q)

# Get IP of Container
docker inspect <container-uid> | grep IPAddress

# Get port used by Container
docker port <container-uid>

### Image Related ###

# Docker kill images
docker rmi <image-uid>

# Remove all images
docker rmi $(docker images -q)

# Remove all <none> tags images
docker rmi -f $(docker images -a | grep "^<none>" | awk '{print $3}')

# Convert image to tar
docker save -o <save image to path> <image name>

# Unpack tar files to image
docker load -i <path to image tar file>
```
