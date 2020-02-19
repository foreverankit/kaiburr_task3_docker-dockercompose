# Kaiburr_task3_docker-dockercompose

We will be creating two docker containers one for our mongo db and the other for our spring application. They both will run in different containers and we will use docker-compose to help them communicate.

It is a very simple Spring Boot web application which saves users into Mongo DB. A new added server is displayed in the server table at the bottom of the page.

## Requirements

###Any Linux distribution/Mac OS/Windows

###Docker

###Docker-compose

###Java JDK


## You can clone my project or make a new project. Just dont forget to build an executable jar file. Once maven clean build is run it will be created in the target folder.


## Create a docker file in the root folder of your project


Build image for our Java application from openjdk alpine image

Update alpine and install bash

Create /opt/app for our java application

Copy compiled (previously) jar file into the PROJECT_HOME folder 

Mark /opt/app folder as working for CMD

Specify a command which will be run when our container is being started

CMD ["java", "-Dspring.data.mongodb.uri=mongodb://springboot-mongo:27017/springmongo-demo","-Djava.security.egd=file:/dev/./urandom","-jar","./springboot-mongodb-0.0.1-SNAPSHOT.jar"]


The following uri describes the connection to mongodb and springboot-mongo is the name of our docker container.


## Create docker-compose.yml file and add the follwing code. Below code is just the services  we need from docker


## Running our application on docker

docker-compose up

Through this command it will keep on running once you stop it using ctrl+c and want docker to run in the background, use the following command.

docker-compose up -d

Our running web application should be available in browser by this URL : http://localhost:8182. Now we can create some server objects.


## Add bash to mongo container

By running this command we will add bash to mongo container.

docker exec -i -t springboot-mongo /bin/bash 






