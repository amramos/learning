#Docker

##Questions
LXC, LXD LXCFS containers
	what are they and what is the difference?

	Docker uses LXC

	Aprender a usar máquina virtual

##Commands

###docker version
	shows the current version of the docker host

###docker ps
	lists all docker containers
	-a option includes non-active containers

###docker stop <container ID or name>
	stops a container. It will appear in Exited state

###docker rm <container ID or name>
	deletes a stopped container

###docker images
	lists the existing images

###docker rmi <image name>
	deletes an image, as long as it is not being used by any containers

###docker pull <image>
	just pulls / downloads the image, but doesn't create a container with it

###docker run (options) <image>(:tag) (command)
	runs a container

	tag
		version of the image. if not provided, default is "latest"

	example of commands: 
		sleep 10 - making the container sleep for 10 seconds
		bash - runs bash on a OS (likely linux based like centos) container

	options:
		-d - run container in a detached state, that is, it will run in the background and you won't see the output on the console
		-it - interactive terminal
		-i - interactive
		--name <name> - give the container a name
		-p <host port>:<container port> - mapping docker host port to container port, example 80:5000 maps the port 80 of the docker host to the port 5000 of the container
		-v <host dir>:<container dir> - maps a directory (volume) on the docker host to a directory inside the container. example /opt/datadir:/var/lib/mysql

###docker exec <container ID or name> <command>
	runs a command on a running container
	exame of command: cat /etc/hosts - this will open the file hosts within the folder etc

###docker attach <hash ID>
	attach a detached container (running on the background) to the console

###docker inspect <container name or ID>
	shows more details on the container, in a JSON format

###docker logs <container name or ID>
	shows logs of the containers which is running on the background (detached)

###docker build Dockerfile (file with this name) -t <Docker username/><image name>:< image tag>
	builds a new docker image
	the Dockerfile has to start with referring to another image - either an OS or another image that already uses an OS

###docker push <Docker username/><image name><: image tag:>
	publishes the image on docker
	you should have logged in first

###docker login
	logs in to Docker

