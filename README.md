# Sensei Docker
Docker is a way to isolate an entire operating system via Linux containers which are a type of virtualization .

With Docker it’s finally possible to faithfully and dependably reproduce a production environment locally, everything from the proper Python version to installing Django and running additional services like a production-level database. This means it no longer matter if you are on a Mac, Windows, or Linux computer. Everything is running within Docker itself.

Docker also makes collaboration in teams exponentially easier. Gone are the days of sharing long, out-of-date README files for adding a new developer to a group project. Instead with Docker you simply share two files–a Dockerfile and docker-compose.yml file–and the developer can have confidence that their local development environment is exactly the same as the rest of the team.

## install docker
https://hub.docker.com/editions/community/docker-ce-desktop-mac
https://hub.docker.com/editions/community/docker-ce-desktop-windows
https://docs.docker.com/install/

check installation

```
$ docker --version
```
Docker is often used with an additional tool, Docker Compose 28 , to help automate commands. Docker Compose is included with Mac and Windows downloads but if you are on Linux you will need to add it manually. You can do this by running the command 
```sudo pip install docker-compose 
```
after your Docker installation is complete.

Docker ships with its own “Hello, World” image that is a helpful first step to run. On the command line type 
```
$ docker run hello-world
``` 
This will download an official Docker image and then run it within a container. The command
```
$ docker info 
``` 
lets us inspect Docker. It will contain a lot of output but focus on the top lines which show we now have 1 container which is stopped and 1 image.
This means Docker is successfully installed and running.# sensei_docker

## Demo

### commands

#### create docker network
```
$ docker network create mongo-network
```

####
```
$ docker run -d \
> -p 27017:27017
> -e MONGO_INITDB_ROOT_USERNAME=rickysensei \
> -e MONGO_INITDB_ROOT_PASSWORD=password \
> --net mongodb \
> mongo
```

#### start mongo-express
```
$ docker run -d \
> -p 8081:8081 \
> -e ME_CONFIG_MONGODB_ADMINUSERNAME=rickysensei \
> -e ME_CONFIG_MONGODB_ADMINPASSWORD=password \
> --net mongo-network \
> --name mongo-express \
> -e ME_CONFIG_MONGODB_SERVER=mongodb \
> mongo-express