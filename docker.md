##### Example

Start new Docker container in background from nginx image of version 1.11, open port 8080 on the host and route traffic to the container port 80, add to network with network alias webhost, pass environment variable and change CMD run on start 

`docker container run -d -p 8080:80 --name webhost --net web --net-alias webhost -e ENV_VAR nginx:1.11 nginx -T`

---

##### Docker command line structure

old: `docker <command> (options)`
new: `docker <command> <sub-command> (options)`

Verify Docker version (cli can talk to engine)

`docker version`

Most config values of engine

`docker info`

Show live performance data for all containers

`docker stats`

See space usage

`docker system df`

Delete everything that is not running (all stopped containers, all volumes not used by at least one container, all networks not used by at least one container, all dangling images)

`docker system prune`

Remove both unused and dangling images

`docker system prune -a`

*extra options and description availabe [here](https://docs.docker.com/engine/reference/commandline/system_prune/)*

*you can also use prune command with container, volume, network, image management commands*

*difference between unused and dangling images [link](https://stackoverflow.com/questions/45142528/what-is-a-dangling-image-and-what-is-an-unused-image)*

---

##### Docker container commands

See, follow container logs

`docker container logs -f webhost`

List container running processes 

`docker container top webhost`

List all containers **(running and stopped)**

`docker container ls -a`

Show metadata about the container

`docker container inspect webhost`

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

Check which ports are forwarding traffic to container from host

`docker container port webhost`

Get ip address of container

`docker container inspect --format '{{ .NetworkSettings.IPAddress }}' webhost`

---

##### Docker network commands

Show networks

`docker network ls`

Create a network

`docker network create my_app_net --driver bridge`

Inspect a network

`docker network inspect my_app_net`

Attach a network to container **(dynamically creates a NIC in a container on an existing virtual network)**

`docker network connect my_app_net webhost`

Detach a network from container **(dynamically removes a NIC from a container on an existing virtual network)**

`docker network disconnect my_app_net webhost`

:warning: **(deprecated)** Since default bridge network do not have DNS server built into it, so you can specify links between containers

option `--link`

Test two container name dns resolution in the same network

`docker container exec -it webhost_1 ping webhost_2`

List DNS entries in network

`docker container run --rm --net web alpine nslookup webhost`

Test net alias connectivity

`docker container run --rm --net web centos curl -s search:9200`

Remove container when it exits or when the daemon exits

option `--rm`

---

##### Docker image commands

Show layers of changes made in image

`docker image history`

List all local Docker images

`docker image ls`

Return JSON metadata about the image

`docker image inspect`

Clean up just dangling images

`docker image prune`

##### Docker volumes and bind mounts

option `-v mysql-db:/var/lib/mysql`

Bind mount - host files overwrite any in container **(cant use in dockerfile, only in run command)**

`/users/bret/stuff:/path/container`

*More info [here](https://docs.docker.com/storage/volumes/)*



