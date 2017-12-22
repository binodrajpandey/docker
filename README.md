# How to Install Docker in Ubuntu?
1. Go to https://docs.docker.com/engine/installation/linux/docker-ee/ubuntu/ link. There are two version of docker one is for community and another for enterprise.
2. Test your operating system using following command. </br>
`cat /etc/*release*`
3. Uninstall old version if you have install using command </br>
`sudo apt-get remove docker docker-engine docker.io`
4. `sudo apt-get update`
5. Install other dependent packages using following command</br>
`sudo apt-get install \`
   ` apt-transport-https \`
   ` ca-certificates \`
    `curl \`
    `software-properties-common``
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
