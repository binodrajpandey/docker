# How to Install Docker in Ubuntu?
1. Go to https://docs.docker.com/engine/installation/linux/docker-ee/ubuntu/ link. There are two version of docker one is for community and another for enterprise.
2. Test your operating system using following command. </br>
`cat /etc/*release*`
3. Uninstall old version if you have install using command </br>
`sudo apt-get remove docker docker-engine docker.io`
4. `sudo apt-get update`
5. Install other dependent packages using following command</br>
`sudo apt-get install \`</br>
   ` apt-transport-https \`</br>
   ` ca-certificates \`</br>
    `curl \`</br>
    `software-properties-common`</br>
 6. Add Docker's official GPG key:   

` curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -`
 
 7. verify key id: it should be 9DC8 5822 9FC7 DD38 854A  E2D8 8D81 803C 0EBF CD88
                                
` sudo apt-key fingerprint 0EBFCD88`

 8. Use the following command to set up the stable repository.</br>
 `sudo add-apt-repository \`
   `"deb [arch=amd64] https://download.docker.com/linux/ubuntu \`
   `$(lsb_release -cs) \`
  ` stable"`
9. Use apt-get update as you have just added repository.</br>
`sudo apt-get update`
10. Now install docker-ce </br>
`sudo apt-get install docker-ce`
11. Docker is installed. Now check using command
`sudo docker run hello-world`

 Docker Hub is a registry service on the cloud that allows you to download Docker images that are built by other 
communities. You can also upload your own Docker built images to Docker hub.

### Some Docker Commands
1. `docker pull jenkins `</br>
-This command will downloads the jenkins image from docker hub.
2. `docker run -i jenkins sleep 2000 ` <br>
   -This command will firts search jenkins in local system, if not found will download from the docker registry. -i indicates that it will interact with standard input system of the host. when the image runs, it will hold 2000 seconds.
3. `docker run -it centos bash` </br>
  -It will run centos with interactive mode ie. open bash of centos, you can use cat /etc/*release* to verify the system
4. `docker run -d centos `
 - It will run centos in detach mode.
5. `docker attach centosImageId`
 - This will again attach container
6. ` docker exec conatainerId cat /etc/*release* `</br>
-run command  cat inside running container
7. `docker ps `</br>
list all the container currently running on the system
8.  `docker ps -a ` </br>
-a tells all lhe containers (exited too) on the system
9. `docker stop <image_name>`</br>
 stop docker container 
10.  `docker run -p 8080:8080 jenkins`</br>
 here first port value is for your docker host and second is for docker container.
11.  `docker run -v /opt/datadir:/var/lib/mysql mysql` </br>
 - used to map volume
12. `docker images -q` </br>
 where -q is used to ists ids only of images
13. `docker rm containerId1 containerid2 containerid3`
14. `docker rmi imageId`
15. `docker inspect jenkins`
16. `docker history centos` </br>
 -see all the command that we gave against given image
17. `ocker stats containerId` </br>
 -provide the statistics of container like cpu and memory utilization of the container
18.`docker pause containerId `
 -pause the processes in the container
19. `dokcer unpause containerId`</br>
20. `docker kill containerId`
-kill the process in docker container
21. `docker restart containerId`
22. `service docker stop`</br>
-stop the docker daemon
23.`service docker start`
24. `docker build -t acc_namem/imagename:tagname dir`
-In order to build your own image you have to create docker file with instructions on how to build your images.

25. `docker login`
26.`docker push imagename`

### Docker File commands
1. `FROM`</br>
->identifies where image come from?first line and can have multiple
2. `MAINTAINER`
-> author
3.`RUN`
->executes command while building a container
4. `CMD`</br>
-> doesn't run during build but run when container starts
5. `EXPOSE`</br>
-> expose container ports to host at runtime
6. `ENV`</br>
-> sets environment variable to pass at runtime
7. `ADD`</br>
->copies file(configuration/data) in to the container
8. `ENTRYPOINT`
->what to run to start command
9. `COPY`
10. `VOLUME`
11. `USER`
12. `WORKDIR`</br>
->Sets working directory for CMD, RUN and ENTRYPOINT commands
13. `ONBUILD`

### docker compose
1. `docker-compose up`
2. `docker-compose stop`
3. `docker-compose down` 
-removes container permanently
version: '3'
services:
  mysql:
      image: "mysql"
      environment:
	- MYSQL_ROOT_PASSWORD=password
     volumes:
	- /root/mydir:/var/mysql/data
  web:
    image: "wordpress"
    ports:
      - "8080:80"
    environment:
            - WORDPRESS_DB_PASSWORD=password



