### Docker commands

##### Docker command line structure

old: `docker <command> (options)`
new: `docker <command> <sub-command> (options)`

Verify Docker version (cli can talk to engine)

`docker version`

Most config values of engine

`docker info`

Start new Docker container in background from nginx image of version 1.11, open port 8080 on the host and route traffic to the container port 80, change CMD run on start and pass environment variable

`docker container run -d -p 8080:80 --name webhost -e ENV_VAR nginx:1.11 nginx -T`

See, follow container logs

`docker container logs -f webhost`

List container running processes 

`docker container top webhost`

List all containers **(both running and stopped)**

`docker container ls -a`

List all local Docker images

`docker images ls`

Show metadata about the container

`docker container inspect webhost`

Show live performance data for all containers

`docker stats`

Run new container interactively **(Ubuntu image already have bash defined as CMD at container start)**

`docker container run -it --name ubuntu ubuntu`

Start stopped container interactively

`docker container start -ai ubuntu`

Run additional process in already running container

`docker container exec -it ubuntu bash`

Simulate a real terminal, like what SSH does

option `-t` (pseudo-tty)

Keep session open to receive terminal input

option `-i` (interactive)