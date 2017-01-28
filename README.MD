## OS requirements
To install Docker, you need the 64-bit version of one of these Ubuntu versions:

* Yakkety 16.10
* Xenial 16.04 (LTS)
* Trusty 14.04 (LTS)

## Install Docker
Use this command to install the latest version of Docker:

	apt-get install docker

Please add your user to the Docker user group like this:

	sudo usermod -aG docker <username>
	newgrp docker

Start run Docker deamon:

	service docker start

Build Docker image by dockerfile:

	sudo docker build -t rockchip .

Now you get a Docker image named "rockchip" which include a debian multiarch cross-compiling enviroment.

## Build application

normal application:

	docker run -v <package dir>:/home/rk/packages rockchip bash -c "cd /home/rk/packages/<package name>; <build command>"

e.g:

	docker run -v ~/workbench/debian-sdk/packages:/home/rk/packages rockchip bash -c "cd /home/rk/packages/mpp; DEB_BUILD_OPTIONS=nocheck debuild  -i -nc -us -uc -b -d  -aarmhf"

## Modify image

If you want to modify your Docker image, you can open a shell by below command:

	docker run -it -v rockchip /bin/bash

After exit from container, you should use below command to save your changes.

	docker commit  <container_id> rockchip
	
## Others

To get more informations about dockers, please check below link:
https://docs.docker.com
