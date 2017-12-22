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

### Some Docker Commsnds
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
9. `docker stop <image_name>`
 stop docker container 


