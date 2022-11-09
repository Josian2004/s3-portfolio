# Individual Project

## Table of Contents
- [NS-Tracker](#ns-tracker)
  - [Project description](#project-description)
  - [Requirements](#requirements)
  - [C4-Model](#c4-model)
    - [Level 2](#level-2)
  - [Technology stack](#technology-stack)
    - [Front-end stack](#front-end-stack)
    - [Back-end stack](#back-end-stack)
  - [Conclusion](#conslusion)
- [MCSTurtleTracker](#mcsturtletracker)
  - [What is MCS?](#what-is-mcs)
  - [Project Description](#project-description-1)
  - [Requirements](#requirements-1)
  - [User-stories](#user-stories)
  - [C4-Model](#c4-model-1)
    - [Level 1](#level-1)
    - [Level 2](#level-2-1)
  - [Projects](#projects)
    - [Front-end](#front-end)
    - [Back-end](#back-end)
    - [Resource server](#resource-server)
    - [External API](#external-api)
  - [Software Quality](#software-quality)
  - [Continuous integration and deployment](#continuous-integration-and-deployment)
    - [Containerization](#containerization)
    - [Pipeline](#pipeline)
    - [Deployment environment](#deployment-environment)

# NS-Tracker
## Project Description
I’m going to create an application which a user can use to find all the information about the NS. The user can find information about a specific train station, train, or train route.

E.g., a user can search for a train station by name or station code and the application will show all the information about that station, like the UIC-code, all the departures and arrivals, all the tracks, etc.

The user could go even deeper and click on a specific train and see what kind of route it is driving and how many train units it has.\
If the user has an account, he/she can favourite any train, station or train route and instantly see if there are any disruptions or problems with that train, station or train route and even get notifications.

The last main feature is a live train tracker, I want to create a live map with the location of all the trains and stations. The user would be able to click on any of these and see the details. I already have the coordinates for the stations and I’m trying to get all the live locations for all the trains, however the NS-API only shows 10 trains so I’m trying to get them all at the same time.


## Requirements
**FR-01:** The user must be able to search stations and see all the relevant information.
-	**S-01.1:** The user must see all the departing trains from this station.
-	**S-01.2:** The user must see all the arriving trains to this station.
-	**S-01.3:** The user must see any other relevant information about this station.
-	**S-01.4:** The user must be able to search by station name, code and UIC code.
-	**S-01.5:** The application must have a search suggestion system.
-	**R-01.1:** The user can’t enter an invalid station name or code.

**FR-02:** The user must be able to search trains and see all the relevant information.
-	**S-02.1:** The user must be able to search by train number.
-	**S-02.2:** The application must have a search suggestion system.
-	**R-02.1:** The user can’t enter an invalid train number.

**FR-03:** The user must be able to search train routes and see all the relevant information.
-	**S-03.1:** The user must be able to search by route number.
-	**S-03.2:** The application must have a search suggestion system.
-	**R-03.1:** The user can’t enter an invalid route number.

**FR-04:** The user must be able to see all the trains on a map.
-	**S-04.1:** The user must see icons (of some kind) on the map where the train is.
-	**S-04.2:** The train location must update every 5 seconds (if the ns API allows it).
-	**S-04.3:** The user must be able to click on the icon and see some basic information and a button to go to a more detailed information page (same as FR-02).

**FR-05:** The user must be able to see all the stations on a map.
-	**S-05.1:** The user must see icons (of some kind) on the map where the station is.
-	**S-05.2:** The user must be able to click on the icon and see some basic information and a button to go to a more detailed information page (same as FR-01).

**FR-06:** The user must be able to favourite any trains, stations, and train routes.
-	**S-06.1:** The user must see a list with all the favourites.
-	**S-06.2:** The user must see a different icon on the map for their favourites.
-	**S-06.3:** The user must see/receive a notification if there are any problems or disruptions with their favourites.



## C4-Model
### Level 2
![Container Model](https://github.com/Josian2004/s3-ip-portfolio/blob/main/portfolio_images/C4-NS/C4Models-ContainerDiagram.png)

## Technology Stack
### Front-end Stack
#### Web-based Application
For the front-end web-based application I used Vue.js as my JavaScript framework, I chose Vue because of its component system, which makes the code more easily readable and gives me the option to easily reuse components in other parts of my web-app without the need to rewrite it.
It’s also a lightweight framework which makes my app a lot more responsive and faster.
Lastly, I have some very entry level experience with Vue which isn’t enough to build a full web-application, so I want to widen my Vue knowledge so that in the future I’m able to create a full Vue web-app.
For styling I use CSS and Bootstrap, this is a styling library which makes it very easy and fast to create a good-looking webpage.
Furthermore, I use a npm-package called Axios. This package gives me the ability to easily create HTTP-requests to my back-end API.

#### Desktop Application
Secondly, I want to create a desktop application, this application will be build using Unity Engine. To develop in Unity, you need to use C# so that’s what I will be using.
I will be able to use Unity to create a 3D interface for my live train and station tracker.
Unity has a big asset store, here you can download (sometimes freely) models to use in your 3D environment.

### Back-end Stack
#### Logic
The back-end consists of multiple microservices, each microservice contains two or three of these components:
-	Controller: Responsible for listening and responding to incoming requests.
-	Service: This is where all the logic for the specific microservice is.
-	Data Access Object (DAO): Responsible for communicating with the database and external API’s.
The microservices are built with the SpringBoot framework and thus are written in Java.
The reason I chose Java is, because I’ve used C# last semester and I want to learn a different language.
I chose SpringBoot because it is one of the biggest and most popular Java frameworks so there is a lot of documentation available. It also has Dependency Injection which makes it very easy to create loosely coupled modules.

The back-end is made of microservices, I chose these because:
1.	Improved scalability: It’s very easy to up or downgrade specific services or add a new service with a new feature without the need to dive deep into the code to change something. I can easily remove a service and the rest of the application should just continue to work.
2.	Future-proofed: If a technology updates, I can easily replace a whole microservice with something better without the need to change code in other parts of my application which makes it very easy to maintain the application and keep updating it with the latest technologies and innovations.
3.	Teamwork: This isn’t relevant for my individual project, but it is for the proftaak. With microservices you can easily split up the work between different team members without interfering with each other code. So, no more annoying code merging problems.

#### External API
I’m using an external API to get real-world data; I’ve chosen for the NS-API. 
The API gives me access to a lot of NS data, e.g.:
-	All the stations where NS or a Dutch regional train company operates with some information like number of tracks and coordinates.
-	All the departures and arrivals from and to a specific station.
-	Information about a specific train like how long the train is, what route it is driving and live coordinates.

## Conslusion
I’ve decided that I won’t continue with this project. Of course, I will be able to use all the knowledge I’ve gathered in my next project. 
I have come up with another idea which involves the Minecraft Server I play on with some friends. Because I play a lot on this server, it gives me a lot more motivation to make an application for this.

&nbsp;
&nbsp;
&nbsp;
# MCSTurtleTracker
## What is MCS?
MCSynergy (or MCS for short) is a Minecraft Server where I play on with some friends, we have a mod installed called ComputerCraft which adds programmable computers and robots (turtles) to Minecraft. These are programmed in Lua and gives us the ability to automate a lot of things which wouldn’t normally be possible. 
This mod has WebSocket connections and HTTP-requests build in which gives me the opportunity to share data between these turtles and some external application which is exactly what I’m going to build.

## Project Description
I’m going to create an application which the users of the Minecraft server of me and my friends can use to see any relevant data about the turtles.
All the turtles will send messages to a central system, this system will then send these messages to my back-end. The back-end will transform and save this data and the front-end can request this data. 
E.g., the turtle is done with a task and needs help from a player, the turtle will then send a message and the webapp will show this message.
The second feature in my application is to have as much as possible control over the turtles, I want to be able to start and stop scripts and manually send commands to a turtle. 
If I have enough time, I want to recreate the whole turtle interface in my webapp so you can easily see what the turtle is doing.

## Requirements
*S: Specification
*R: Restriction

&nbsp;
### Functional Requirements
**FR-01**: The user must be able to see a list of all the connected turtles
-	**S-01.1:** In this screen a turtle must contain a name, a turtle-id, a status, and an assigned system.
-	**S-01.2:** The user must be able to search for a turtle by name, turtle-id, and assigned system.
-	**S-01.3:** The user must be able to filter the list by status.
-	**S-01.4:** The user must be able to click on a turtle and be redirected to the corresponding detail page (FR-02).

**FR-02:** The user must be able to see a detail page about every turtle.
-	**S-02.1:** The user must be able to see these attributes about a turtle:
o	Current location (in x, y, z coordinates)
o	Current dimension
o	Fuel level
o	Inventory
o	Current upgrades
o	Status
o	Name
o	Turtle-id
o	Assigned system
-	**S-02.2:** The user must be able to see all the recently send messages from this turtle.
-	**R-02.1:** The inventory of a turtle should only be inspected when the user presses on a button.

**FR-03:** The user must be able to turn a turtle on/off.
-	**S-03.1:** The user must be able to turn them on/off from their corresponding detail page (FR-02).
-	**R-03.1:** The turtle must not completely be turned off; it should only stop with their current task or farm and return to their starting location.

 **FR-04:** The user must see a list of all send messages.
-	**S-04.1:** The user must see a turtle-id, name, status when being send, assigned system, message type and message for all send messages.
-	**S-04.2:** The user must be able to filter the list by turtle-id, name, assigned system, and message type.
-	**R-04.1:** If the message doesn’t have a known system, hide the message.

**FR-05:** The user must be able to CRUD systems.
-	**S-05.1:** The user must be able to turn the whole system on/off.
-	**S-05.2:** The user must be able to specify which turtle is part of which system.
-	**R-05.1:** The system must have a unique name.

**FR-06:** The user must be able to use a help page to know how to implement the system on their turtles.
-	**S-06.1:**  The user must be able to see what Lua methods should be called for the system to work
-	**S-06.2:** The user must be able to see what Lua libraries are required for the system to work.
-	**S-06.3:** The user must be able to see what configuration must be done on the turtles for the system to work.

**FR-07:** The current Lua scripts shouldn’t have to be completely rewritten for the system to work.
-	**R-07.1:** The user should only have to call one extra method at the start of the script for the system to work.
-	**R-07.2:** The user should only have to configure the system once.

&nbsp;
&nbsp;
### Non-functional Requirements
**NFR-01:** The current Lua scripts shouldn’t become very much slower.
-	**S-01.1:** The system should run parallel to the main script, so it doesn’t halt the main script.

**NFR-02:** All the turtles should send their information to one central computer; this computer will then send them to the back-end.

**NFR-03:** Only authorized users should be able to use this application.

**NFR-04:** The central computer should save all the messages when the application is offline.
-	**S-04.1:** When the application comes back online, the central computer should send all the missed messages.

**NFR-05:** The Lua system should be very reliable.
-	**S-05.1:** It should always catch errors and handle them.
-	**S-05.2:** If the system crashes or is offline, the turtles should continue with their scripts and should not stop.

## User-stories
**US1:** As a user I want to be able to see all the turtles so I can track them and know if something is wrong with them.

**US2:** As a user I want to be able to see a detailed page about every turtle so I can see more information about them like their inventory.

**US3:** As a user I want to be able to turn the turtles on/off, so I have more control over the turtles.

**US4:** As a user I want to be able to see all the messages sent by the turtles, so I know when a turtle logs an error or warning and I need to do something about it.

**US5:** As a user I want to be able to CRUD new MSC Systems so that I can easily add a newly build system to the app and don’t have to do some technical things.

**US6:** As a user I want to be able to have a place where I can find information about how to implement the system and how it works so it is very easy for me to implement the system and I don’t have to ask someone for instructions.

**US7:** As a user I don’t want to have to completely rewrite my scripts for the system to work because that would take a lot of wasted time and effort.

**US8:** As a user I want to be able to sort turtles by MCS System so I don’t have to search through a big list to find a specific turtle.

**US9:** As a user I want to be able to filter the messages by type, so I e.g., only see errors or warnings.

**US10:** As a user I want to be able to see for how long a turtle has to wait before it starts a new run.


## C4-Model
### Level 1
![Context Model](https://github.com/Josian2004/s3-ip-portfolio/blob/main/portfolio_images/C4-MCST/C4-Model-C1.drawio.png)
### Level 2
![Container Model](https://github.com/Josian2004/s3-ip-portfolio/blob/main/portfolio_images/C4-MCST/C4-Model-C2.drawio.png)

## Projects
This project is actually working and deployed on my server so you can see it for yourself at:\
https://mcst.josian.nl

### [Front-end](https://git.fhict.nl/I483898/mcst-vue-frontend)
For the front-end web-based application I used Vue.js as my JavaScript framework, I chose Vue because of its component system, which makes the code more easily readable and gives me the option to easily reuse components in other parts of my web-app without the need to rewrite it.
It’s also a lightweight framework which makes my app a lot more responsive and faster.\
Lastly, I have some very entry level experience with Vue which isn’t enough to build a full web-application, so I want to widen my Vue knowledge so that in the future I’m able to create a full Vue web-app.\
For styling I use CSS and Tailwind, this is a styling library which makes it very easy and fast to create a good-looking webpage.\
Furthermore, I use a npm-package called Axios. This package gives me the ability to easily create HTTP-requests to the MCS Systems API (external API).

### [Back-end](https://git.fhict.nl/I483898/mcst-springboot-backend)
#### Logic
The back-end consists of multiple microservices, each microservice contains two or three of these components:
-	Controller: Responsible for listening and responding to incoming requests.
-	Websocket Handlers: Responsible for listening for/sending messages over websocket.
-	Service: This is where all the logic for the specific microservice is.
-	Events: These are used for dependency inversion so that the service is independent from the e.g. websocket handlers.
-	Repository: Part of Spring Data JPA and responsible for communicating with the database.
-	Models: This is where all the data is being stored and used across the microservice.

The microservices are built with the SpringBoot framework and thus are written in Java.
The reason I chose Java is, because I’ve used C# last semester and I want to learn a different language.
I chose SpringBoot because it is one of the biggest and most popular Java frameworks so there is a lot of documentation available. It also has Dependency Injection which makes it very easy to create loosely coupled modules.\

The back-end is made of microservices, I chose these because:
1.	Improved scalability: It’s very easy to up or downgrade specific services or add a new service with a new feature without the need to dive deep into the code to change something. I can easily remove a service and the rest of the application should just continue to work.
2.	Future-proofed: If a technology updates, I can easily replace a whole microservice with something better without the need to change code in other parts of my application which makes it very easy to maintain the application and keep updating it with the latest technologies and innovations.
3.	Teamwork: This isn’t relevant for my individual project, but it is for the proftaak. With microservices you can easily split up the work between different team members without interfering with each other code. So, no more annoying code merging problems.

#### Data Persistence
I'm using the ORM Spring Data JPA because it is build-in in Spring Boot, the ORM is responsible for retreiving/saving all the data from my application.
I'm using a MySQL database for storing the data.

### Resource Server
All my data is coming from the Minecraft server, it works as follows.\
All the turtles (robots) send their data (location, message, etc.) to a central system over a "minecraft network". 
When this central system receives a message, it will send the message over a websocket connection to the back-end server.\
The system uses ComputerCraft (Minecraft Mod) which has a build-in websocket en HTTP feature to establish a connection with my back-end server.\
All the scripts for this mod are written in Lua.

### [External API](https://docs.naamdorpboot.xyz/systems-api)
In our server we have a lot of farms (systems as we call them) and most turtles are assigned to a specific farm. To get the information of all the farms currently active in the server, a friend of mine has written an API where we can request said data. This way my app will always have the latest farm data without the need to hard-code a newly build farm.

## Software Quality

## Continuous Integration and Deployment
In order to automate the test and deploy process of my application, I implemented a CI/CD pipeline for both my webapp and server. This has been done with GitLab CI/CD.
In order to keep my data secure, I've made environment variables for all the sensitive data like password, keys etc. These pipelines are automatically triggered when a push is made to either the main branch or development branch. However only when pushed to the main branch will the app be build and deployed, when pushed to the development branch it will only run the tests.

### Containerization
To easily deploy my application, I have made use of Docker. I've created a Dockerfile for both my front-end and back-end
#### Front-end
```Dockerfile
# Dockerfile
FROM node:lts-alpine
LABEL maintainer="MCSDevTeam"
RUN npm install -g http-server
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build
CMD [ "http-server", "dist" ]
```
What this file does is, firstly it will install a http-server so I can run the app. Then it will copy the *package.json* and install all the necessary packages for the application to build. Then it will copy the rest of the files and build the application, this will then create a /dist folder which the http-server uses to start the app.
```yaml
# docker-compose.yml
version: '3.4'
services:
    mcst_webapp:
        container_name: MCST-WebApp
        image: $REGISTRY_URL/mcst_webapp:latest
        environment:
            TZ: "Europe/Amsterdam"
        ports:
            - '25001:8080'
        expose:
            - '25001'
        stdin_open: 'true'
        tty: 'true'
```
When I'm ready to start the container, I will run this docker-compose file which will start the app with some specific settings like the port and timezone.

#### Back-end
```Dockerfile
# Dockerfile
FROM eclipse-temurin:17-jdk-alpine
LABEL maintainer="MCSDevTeam"
COPY target/MCSTurtleTracker-backend-0.0.1-SNAPSHOT.jar .
ENTRYPOINT ["java", "-jar", "MCSTurtleTracker-backend-0.0.1-SNAPSHOT.jar"]
```
This file does almost the same as the front-end file, however it won't build the application. It will simply copy the .jar file and run it using Java.

```yaml
# docker-compose.yml
version: '3.4'
services:
    mcst_db_dev:
        container_name: MCST-DB
        image: mysql:5
        environment:
            MYSQL_DATABASE: 'mcst_db_dev'
            MYSQL_ROOT_PASSWORD: 'xxxx'
            TZ: "Europe/Amsterdam"
        ports:
            - '25002:3306'
        expose:
            - '25002'
        volumes:
            - mcst_db_volume:/var/lib/mysql
            
    mcst_backend:
        container_name: MCST-Server
        image: $REGISTRY_URL/mcst_backend:latest
        environment:
            SPRING_DATASOURCE_URL: 'jdbc:mysql://mcst_db_dev:3306/mcst_db_dev'
            SPRING_DATASOURCE_USERNAME: 'xxxx'
            SPRING_DATASOURCE_PASSWORD: 'xxxx'
            SPRING_JPA_HIBERNATE_DDL-AUTO: 'update'
            SPRING_JPA_DATABASE-PLATFORM: 'org.hibernate.dialect.MySQL5InnoDBDialect'
            CREATEDATABASEIFNOTEXISTS: 'true'
            SERVER_SERVLET_CONTEXT-PATH: '/api'
            SERVER_PORT: 25000
            TZ: "Europe/Amsterdam"
        ports:
            - '25000:25000'
        expose:
            - '25000'
        depends_on:
            - mcst_db_dev
        stdin_open: 'true'
        tty: 'true'
volumes:
    mcst_db_volume:
```
This docker-compose file is a little bit different from the front-end file because, this file starts two containers. It will also start a MySQL v5 container with a Docker Volume to make sure the data isn't lost when the container is stopped and removed.
Then it will start the back-end server with some environment variables and settings for the database connection.
Because the back-end server won't start/run without a database, I've specified that the server depends on the database.
Another nice feature is that because we have both containers in one file, it will also create a Docker network with both in it so the back-end can communicate with the database without using it's external IP-address. Technically I don't have to expose port 25002 for the database but I like to have the ability to see the contents of the database externally.

### Pipeline
#### Test Job
```yaml
run_tests:
    stage: test
    image: eclipse-temurin:17-jdk-alpine
    before_script:
        - chmod +x mvnw
    script:
        - ./mvnw test
```
This job is responsible for running all the necessary tests.

#### Build Job
```yaml
build:
    stage: build
    image: eclipse-temurin:17-jdk-alpine
    rules:
        - if: '$CI_COMMIT_BRANCH == "main"'
    before_script:
        - chmod +x mvnw
    script: "./mvnw install"
    artifacts:
        paths:
        - target/*.jar
```
This job is responsible for building the application, it will run the *./mvnw install* command which will build the app into an executable .jar file and save it 
so further jobs can use it. In *rules* I've specified that this job should only run when pushed to the main branch.

#### Package Job
```yaml
package:
    stage: package
    rules:
        - if: '$CI_COMMIT_BRANCH == "main"'    
    script:
        - docker build . -t $REGISTRY_URL/mcst_backend
        - docker login -u $REGISTRY_USERNAME -p $REGISTRY_PASSWORD $REGISTRY_URL
        - docker push $REGISTRY_URL/mcst_backend
```
This job is responsible for preparing my application to be deployed, it will firstly build the dockerimage with the correct environment variables and then push this image to a self-hosted Docker Registry. Because this is a secured registry, it will first need to login using secret variables before it can push an image.

#### Deploy Job
```yaml
deploy:
    stage: deploy
    image: alpine:latest
    rules:
        - if: '$CI_COMMIT_BRANCH == "main"'
    before_script:
        - mkdir -p ~/.ssh
        - chmod 700 ~/.ssh
        - apk update && apk add openssh-client bash
        - eval $(ssh-agent -s)
        - bash -c 'ssh-add <(echo "$SSH_PRIVATE_KEY")'
    script:
        - ssh -o StrictHostKeyChecking=no -p $SSH_PORT $SSH_USER@$SSH_URL "
            docker-compose -f /media/josian/Hard\ Disk/Apps/MCST/Docker-compose/Backend/docker-compose.yml down &&
            docker login -u $REGISTRY_USERNAME -p $REGISTRY_PASSWORD $REGISTRY_URL &&
            docker pull $REGISTRY_URL/mcst_backend:latest &&
            docker-compose -f /media/josian/Hard\ Disk/Apps/MCST/Docker-compose/Backend/docker-compose.yml up -d"
```
This is the final job and it's responsible for deploying the application to a server. Alpine Linux doesn't natively have a ssh-client installed so that is what I'm doing manually in the *before script*. Then I have to add my *SSH_PRIVATE_KEY* to the client so it can connect to my server using that key.\
It will then connect to my server over SSH and do a few things:
1. It will run *docker-compose down* which will stop and remove the old container.
2. It will login to my Docker Registry.
3. It will pull the latest image which we pushed in the last job.
4. Finally it will run *docker-compose up -d* which will start a new container with the latest image.
And then my application is up and running again.

### Deployment Environment
Even though it is sufficient for this semester to "deploy" to the Docker Hub, I felt that it wasn't complete until me and my friends could access my app from wherever we  are.

So in the autumn break of 2022, I bought a HP Workstation from Marktplaats and repurposed it as a home server. I deleted Windows and installed Ubuntu because Linux is just way better and faster for a server than Windows.\
Before I had bought this server, I came across a few issues with my CI/CD. First of all, the Docker Hub only allows for one free private repository which isn't enough for both my webapp and server so I would need to host my own registry somewhere. Second of all, Fontys doesn't have any shared GitLab-runners... So I needed to host these myself aswell. And lastly, I needed a place to deploy my app with the posibility to expose it to the internet.

I now have a Docker Registry, two GitLab-Runners and ofcourse my whole MCST Application running on my server and they are accessible via my domain josian.nl, I have also set up a [Nginx](https://www.nginx.com/) Reverse Proxy so I can use fancy sub-domains like mcst.josian.nl for my apps instead of ugly ports after my urls. 
With the use of [LetsEncrypt](https://letsencrypt.org/) and [Certbot](https://certbot.eff.org/) I secured my applications with SSL-certificates and HTTPS, this also gives me the posibility to build my app into a PWA.

I know this has nothing to do with my learning outcomes for this semester, but I've learned alot of other skills like basic infrastructure and security while setting this up which I feel are also important as a software engineer and it was ofcourse fun to do.
