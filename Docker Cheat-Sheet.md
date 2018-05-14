# Docker Cheat-Sheet


### General Usage
#### Start a container in background:  
	* docker run -d < container_name >
#### Start an interactive container 
	* docker run -it ubuntu:16.04 bash
#### Start a container automatically removed on stop
	* docker run --rm ubuntu:16.04 bash
#### Export port from a container
	*  docker run -p 80:80 -d nginx
#### Start a named container
	* docker run --name my_server nginx
#### Restart a stopped container
	* docker start my_server
#### Stop a container
	* docker stop my_server

### Build Images
#### Build an image from Dockerfile in current directory
	* docker build --tag myimage .
#### Force rebuild of Docker image
	* docker build --no-cache . 
#### Convert a container to image
	* docker commit < container_id > myimage
#### Remove all unused images 
	*  docker rmi $(docker images -q -f "dangling=true"

### Manage Containers
#### List running containers
	* docker ps

#### List all containers ( running & stopped )
	* docker ps -a

#### Inspect containers metadatas
	* docker inspect < container_id >
#### List local available images
	* docker images

#### Delete all stopped containers
	* docker rm $(docker ps -- filter status=exited -q)

### Volumes
#### Create a local volume
	* docker volume create --name myvol

#### Mounting a volume on container start
	* docker run -v myvol:/data ubuntu:16.04

#### Destroy a volume
	* docker volume rm myvol

#### List volumes
	* docker volume ls

### Network
#### Create a local network
	* docker network create mynet
#### Attach a container to a network on start
	* docker run -d --net mynet ubuntu:16.04
#### Connect a running container from a network
	* docker network connect mynet < container_id >
#### Disconnect container to a network
	* docker network disconnect mynet < container_id >

### Debug
#### Run another process in running container
	*  docker exec -it < container_id > bash
#### Show live logs of running daemon container 
	* docker logs -f  < container_id >

#### Show exposed ports of a container
	* docker port < container_id >
	