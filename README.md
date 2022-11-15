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

You can search for images available on Docker Hub by using the docker command with the search subcommand. For example, to search for the Ubuntu image, type:
```
$ docker search ubuntu
```
Execute the following command to download the official ubuntu image to your computer:
```
$ docker pull ubuntu
```
To see the images that have been downloaded to your computer, type:
```
$ docker images
```
### Running a docker container
As an example, let’s run a container using the latest image of Ubuntu. The combination of the -i and -t switches gives you interactive shell access into the container:
```
$ docker run -it ubuntu
```
### Managing docker container
To view the active ones, use:
```
$ docker ps
```
To view all containers — active and inactive, run docker ps with the -a switch:
```
$ docker ps -a
```
To view the latest container you created, pass it the -l switch:
```
$ docker ps -l
```
To start a stopped container, use docker start, followed by the container ID or the container’s name. Let’s start the Ubuntu-based container with the ID of 1c08a7a0d0e4:
```
$ docker start 1c08a7a0d0e4
```
To stop a running container, use docker stop, followed by the container ID or name. This time, we’ll use the name that Docker assigned the container, which is quizzical_mcnulty:
```
$ docker stop quizzical_mcnulty
```
Once you’ve decided you no longer need a container anymore, remove it with the docker rm command, again using either the container ID or the name. 
```
$ docker rm youthful_curie
```
### Commint changes in a container to a docker image
Then commit the changes to a new Docker image instance using the following command.
```
$ docker commit -m "What you did to the image" -a "Author Name" container_id repository/new_image_name
```
For example, for the user sammy, with the container ID of d9b100f2f636, the command would be:
```
$ docker commit -m "added Node.js" -a "ricky" d9b100f2f636 ricky/ubuntu-nodejs
```




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
```
[referenece](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-20-04)
