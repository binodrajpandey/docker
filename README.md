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

## How to Run Mysql
`docker run --name mysql -e MYSQL_ROOT_PASSWORD=root -d -v ~/datadir:/var/lib/mysql -h localhost mysql` </br>
Here --name is used to give name of running instance </br>
-e stands for environment </br>
-d used for detatched mode run</br>
-v used for volume mapping</br>
After running instance, if you want to login, hit the following command.
`docker exec -it mysql bash`</br>
`mysql -u root -ppassword`</br>

##  How to Run cassandra
 `docker run -v ~/project/cassandra/datadir:var/lib/cassandra -d --name cassandra cassandra ` <br>
 `docker exec -it cassandra bash` </br>
 `cqlsh -u cassandra -pcassandra` </br>
 Now you can create keyspace like:</br>
 `create keyspace usergram_test with replication={'class':'NetworkTopologyStrategy','datacenter1':'3'} and durable_writes=true;` </br>

## How to Link containers
Suppose we have a project image called *batch* and it has a dependency of mysql and cassandra containers. To link those containers:
` docker run --link mysql --link cassandra -d --name batch batch`

### docker compose
1. `docker-compose up`</br>
2. `docker-compose stop`</br>
3. `docker-compose down` </br>
-removes container permanently. </br>
Example of dockercompose.yml file looks like:
```
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
    deploy:
	replicas: 5
	
	
```
