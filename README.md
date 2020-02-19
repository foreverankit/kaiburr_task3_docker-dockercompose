# Kaiburr_task3_docker-dockercompose

We will be creating two docker containers one for our mongo db and the other for our spring application. They both will run in different containers and we will use docker-compose to help them communicate.

It is a very simple Spring Boot web application which saves users into Mongo DB. A new added server is displayed in the server table at the bottom of the page.

## Requirements

### Any Linux distribution/Mac OS/Windows

### Docker

### Docker-compose

### Java JDK


## You can clone my project or make a new project. Just dont forget to build an executable jar file. Once maven clean build is run it will be created in the target folder.


## Create a docker file in the root folder of your project

![Screenshot from 2020-02-20 04-28-43](https://user-images.githubusercontent.com/31029148/74884602-90a42680-5399-11ea-88f0-ac9f38d41bbe.png)

Build image for our Java application from openjdk alpine image

Update alpine and install bash

Create /opt/app for our java application

Copy compiled (previously) jar file into the PROJECT_HOME folder 

Mark /opt/app folder as working for CMD

Specify a command which will be run when our container is being started

CMD ["java", "-Dspring.data.mongodb.uri=mongodb://springboot-mongo:27017/springmongo-demo","-Djava.security.egd=file:/dev/./urandom","-jar","./springboot-mongodb-0.0.1-SNAPSHOT.jar"]


The following uri describes the connection to mongodb and springboot-mongo is the name of our docker container.


## Create docker-compose.yml file and add the follwing code. Below code is just the services  we need from docker

![Screenshot from 2020-02-20 04-28-54](https://user-images.githubusercontent.com/31029148/74884607-939f1700-5399-11ea-8dae-2be5e0eff4dd.png)


## Running our application on docker

docker-compose up

Through this command it will keep on running once you stop it using ctrl+c and want docker to run in the background, use the following command.

docker-compose up -d

Our running web application should be available in browser by this URL : http://localhost:8182. Now we can create some server objects.


## TO see the containers active

Hit command : sudo docker images

You will find the following

![Screenshot from 2020-02-20 04-34-31](https://user-images.githubusercontent.com/31029148/74884914-4ff8dd00-539a-11ea-8ee5-888e9cd91734.png)


## Add bash to mongo container

By running this command we will add bash to mongo container.

docker exec -i -t springboot-mongo /bin/bash 

The console/terminal will be changed to something like: root@ff55937c3772:/#. It means we’re inside the docker container.

After this write root@ff55937c3772:/#mongo

Now write : root@ff55937c3772:/#use springmongo-db

Now write : root@ff55937c3772:/#db.servers.find()

![Screenshot from 2020-02-20 04-36-10](https://user-images.githubusercontent.com/31029148/74885031-92bab500-539a-11ea-8b76-95750454610a.png)


Here it is both the containers are running seperately.

Thank you..!





