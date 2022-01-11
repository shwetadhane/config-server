# config-server

 **Deployment of latest version of service**

Please follow below mentioend three commands when we have any changes to service and you want to deploy latest version of code to Docker.

#Command to pull latest image from docker.hub
docker pull pradnyilk/<Your Service Name>:latest

#Command to delete existing running service
docker service rm <Your Service Name>-svc

#Command to create new service with latest image pulled
docker service create --with-registry-auth -d --name <Your Service Name>-svc --network my-attachable-overlay-network   --replicas 1 -p <Your Port>:<Your Port> pradnyilk/<Your Service Name>


For example:
replace <Your Service Name> with movie-info-service
replace <Your port> with 8086

Finally it should look like:

#Command to pull latest image from docker.hub
docker pull pradnyilk/config-server:latest

#Command to delete existing running service
docker service rm config-server-svc

#Command to create new service with latest image pulled
docker service create --with-registry-auth -d --name config-server-svc --network my-attachable-overlay-network   --replicas 1 -p 8888:8888 pradnyilk/config-server


**Steps to create a attachable network**

docker network create --driver overlay --attachable my-attachable-overlay-network