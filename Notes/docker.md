# Docker

## Questions
LXC, LXD LXCFS containers
	what are they and what is the difference?

	Docker uses LXC

	Aprender a usar máquina virtual

## Commands

## #docker version
	shows the current version of the docker host

## #docker ps
	lists all docker containers
	-a option includes non-active containers

## #docker stop <container ID or name>
	stops a container. It will appear in Exited state

## #docker rm <container ID or name>
	deletes a stopped container

## #docker images
	lists the existing images

## #docker rmi <image name>
	deletes an image, as long as it is not being used by any containers

## #docker pull <image>
	just pulls / downloads the image, but doesn't create a container with it

## #docker run (options) (ENTRYPOINT) <image>(:tag) (command)
	runs a container

	tag
		version of the image. if not provided, default is "latest"

	example of commands: 
		sleep 10 - making the container sleep for 10 seconds
		bash - runs bash on a OS (likely linux based like centos) container
		ps -eaf - shows all the processes running on the container


	options:
		-d - run container in a detached state, that is, it will run in the background and you won't see the output on the console
		-it - interactive terminal
		-i - interactive
		--name <name> - give the container a name
		-p <host port>:<container port> - mapping docker host port to container port, example 80:5000 maps the port 80 of the docker host to the port 5000 of the container
		-v <host dir>:<container dir> - maps a directory (volume) on the docker host to a directory inside the container. example /opt/datadir:/var/lib/mysql
		--name - name the container
		-e - set environment variables, using ENV_VARIABLE_NAME=Value
		--entrypoint - replaces the ENTRYPOINT from Dockerfile
		--cpus= - number of cpus allocated for this container (ex .5)
		--memory= - memory allocated for this container (ex 100m for 100MB)
		--network - specifies in which network the container will run

## #docker exec <container ID or name> <command>
	runs a command on a running container
	exame of command: cat /etc/hosts - this will open the file hosts within the folder etc

## #docker attach <hash ID>
	attach a detached container (running on the background) to the console

## #docker inspect <container name or ID> (<| grep -A X search term>)
	shows more details on the container, in a JSON format
	grep - search command
		-A X = -A specifies the number of lines (X) in the text that will be displayed after the search term is found.
		search term = text which we want to find in the inspect

## #docker logs <container name or ID>
	shows logs of the containers which is running on the background (detached)

## #docker system df -v
	shows the memory consumption for docker

## #docker build . (-f <filename>) -t <Docker username/><image name>:< image tag>
	builds a new docker image based on the Dockerfile present at the current folder. Optionally, a different file than Dockerfile can be specified using the -f option
	the Dockerfile has to start with referring to another image - either an OS or another image that already uses an OS

	Dockerfile
		FROM <SO or other docker image>

		RUN <bash commands>

		ENTRYPOINT ["<command without parameter>"]

		CMD ["<default value for parameter if not received from input>"]

## #docker push <Docker username/><image name><: image tag:>
	publishes the image on docker
	you should have logged in first

## #docker login
	logs in to Docker

## #docker volume create <volume_name>

	creates a volume to persist data on the host, so that it doesn't get lost when the container is deleted.
	when running the container (or in the docker-compose.yml file), set the volume 

## docker-compose.yml

In order to run multiple containers at a time and link them, use a YAML file called docker-compose.
Create a file name docker-compose.yml (it can be other names, but this is the convention), and use it with this structure:

## Network

## #Listing networks

docker network ls
	lists all networs

docker network inspect <network name>
	inspects the network and shows its details

docker network create \
	-- driver bridge (or home or none) \
	-- subnet <IP ex 182.18.0.0/16>
	<network name>

	creates a new network

