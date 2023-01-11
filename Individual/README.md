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
  - [Quality Assurance](#quality-assurance)
    - [What is QA?](#what-is-qa)
    - [Test Plan](#test-plan)
    - [Implementation](#implementation)
      - [Unit/Integration Tests](#unitintegration-tests)
      - [UX](#ux)
      - [SonarQube](#sonarqube)
      - [Google Lighthouse](#google-lighthouse)
  - [Continuous integration and deployment](#continuous-integration-and-deployment)
    - [Containerization](#containerization)
    - [Pipeline](#pipeline)
    - [Deployment environment](#deployment-environment)
  - [Business Processes](#business-processes)
  - [Professional](#professional)
  - [Agile](#agile)
    - [What is Agile?](#what-is-agile)
    - [What are the differences between Agile and Waterfall?](#what-are-the-differences-between-agile-and-waterfall)
    - [Scrum](#scrum)
    - [Kanban](#kanban)
    - [Extreme Programming](#extreme-programming)
    - [Agile in our project](#agile-in-our-project)
  - [Ethics](#ethics)
    - [What is ethics in software engineering?](#what-is-ethics-in-software-engineering)
    - [Why is it important?](#why-is-it-important)
    - [Ethics in our project](#ethics-in-our-project)
  - [Cultural Differences](#cultural-differences)
    - [What are cultural differences?](#what-are-cultural-differences)
    - [Why is it important in Software Development?](#why-is-it-important-in-software-development)
- [Sources](#sources)

# NS-Tracker
## Project Description
I’m going to create an application that a user can use to find all the information about the NS. The user can find information about a specific train station, train, or train route.

E.g., a user can search for a train station by name or station code and the application will show all the information about that station, like the UIC code, all the departures and arrivals, all the tracks, etc.

The user could go even deeper and click on a specific train and see what kind of route it is driving and how many train units it has.\
If the user has an account, he/she can favourite any train, station or train route and instantly see if there are any disruptions or problems with that train, station or train route and even get notifications.

The last main feature is a live train tracker, I want to create a live map with the location of all the trains and stations. The user would be able to click on any of these and see the details. I already have the coordinates for the stations and I’m trying to get all the live locations for all the trains, however, the NS-API only shows 10 trains so I’m trying to get them all at the same time.


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
![Container Model](https://github.com/Josian2004/s3-portfolio/blob/main/portfolio_images/C4-NS/C4Models-ContainerDiagram-drawio.png)

## Technology Stack
### Front-end Stack
#### Web-based Application
For the front-end web-based application I used Vue.js as my JavaScript framework, I chose Vue because of its component system, which makes the code more easily readable and gives me the option to easily reuse components in other parts of my web app without the need to rewrite it.
It’s also a lightweight framework which makes my app a lot more responsive and faster.
Lastly, I have some very entry-level experience with Vue which isn’t enough to build a full web application, so I want to widen my Vue knowledge so that in the future I’m able to create a full Vue web app.
For styling I use CSS and Bootstrap, this is a styling library which makes it very easy and fast to create a good-looking webpage.
Furthermore, I use an npm package called Axios. This package gives me the ability to easily create HTTP requests to my back-end API.

#### Desktop Application
Secondly, I want to create a desktop application, this application will be built using Unity Engine. To develop in Unity, you need to use C# so that’s what I will be using.
I will be able to use Unity to create a 3D interface for my live train and station tracker.
Unity has a big asset store, here you can download (sometimes freely) models to use in your 3D environment.

### Back-end Stack
#### Logic
The back end consists of multiple microservices, each microservice contains two or three of these components:
-	Controller: Responsible for listening and responding to incoming requests.
-	Service: This is where all the logic for the specific microservice is.
-	Data Access Object (DAO): Responsible for communicating with the database and external APIs.
The microservices are built with the SpringBoot framework and thus are written in Java.
The reason I chose Java is that I’ve used C# last semester and I want to learn a different language.
I chose SpringBoot because it is one of the biggest and most popular Java frameworks so there is a lot of documentation available. It also has Dependency Injection which makes it very easy to create loosely coupled modules.

The back end is made of microservices, I chose these because:
1.	Improved scalability: It’s very easy to up or downgrade specific services or add a new service with a new feature without the need to dive deep into the code to change something. I can easily remove a service and the rest of the application should just continue to work.
2.	Future-proofed: If a technology updates, I can easily replace a whole microservice with something better without the need to change code in other parts of my application which makes it very easy to maintain the application and keep updating it with the latest technologies and innovations.
3.	Teamwork: This isn’t relevant to my individual project, but it is for the proftaak. With microservices, you can easily split up the work between different team members without interfering with each other code. So, no more annoying code merging problems.

#### External API
I’m using an external API to get real-world data; I’ve chosen the NS-API. 
The API gives me access to a lot of NS data, e.g.:
-	All the stations where NS or a Dutch regional train company operates with some information like the number of tracks and coordinates.
-	All the departures and arrivals from and to a specific station.
-	Information about a specific train like how long the train is, what route it is driving and live coordinates.

## Conslusion
I’ve decided that I won’t continue with this project. Of course, I will be able to use all the knowledge I’ve gathered in my next project. 
I have come up with another idea which involves the Minecraft Server I play on with some friends. Because I play a lot on this server, it gives me a lot more motivation to make an application for this.

&nbsp;
&nbsp;
&nbsp;
# MCSTurtleTracker
![MCST Banner](https://github.com/Josian2004/s3-portfolio/blob/main/portfolio_images/MCSTbanner.png)
## What is MCS?
MCSynergy (or MCS for short) is a Minecraft Server that I play on with some friends, we have a mod installed called ComputerCraft which adds programmable computers and robots (turtles) to Minecraft. These are programmed in Lua and give us the ability to automate a lot of things which wouldn’t normally be possible. 
This mod has WebSocket connections and HTTP requests built in which allows me to share data between these turtles and some external applications which is exactly what I’m going to build.

## Project Description
I’m going to create an application that the users of the Minecraft server of me and my friends can use to see any relevant data about the turtles.
All the turtles will send messages to a central system, this system will then send these messages to my back-end. The back end will transform and save this data and the front end can request this data. 
E.g., if the turtle is done with a task and needs help from a player, the turtle will then send a message and the web app will show this message.
The second feature in my application is to have as much as possible control over the turtles, I want to be able to start and stop scripts and manually send commands to a turtle. 
If I have enough time, I want to recreate the whole turtle interface in my web app so you can easily see what the turtle is doing.

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

**FR-02:** The user must be able to see a detailed page about every turtle.
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
-	**R-02.1:** The inventory of a turtle should only be inspected when the user presses a button.

**FR-03:** The user must be able to turn a turtle on/off.
-	**S-03.1:** The user must be able to turn them on/off from their corresponding detail page (FR-02).
-	**R-03.1:** The turtle must not completely be turned off; it should only stop with its current task or farm and return to its starting location.

 **FR-04:** The user must see a list of all sent messages.
-	**S-04.1:** The user must see a turtle-id, name, status when being sent, assigned system, message type and message for all sent messages.
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

**NFR-02:** All the turtles should send their information to one central computer; this computer will then send them to the back end.

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

**US5:** As a user I want to be able to CRUD new MSC Systems so that I can easily add a new build system to the app and don’t have to do some technical things.

**US6:** As a user I want to be able to have a place where I can find information about how to implement the system and how it works so it is very easy for me to implement the system and I don’t have to ask someone for instructions.

**US7:** As a user I don’t want to have to completely rewrite my scripts for the system to work because that would take a lot of wasted time and effort.

**US8:** As a user I want to be able to sort turtles by MCS System so I don’t have to search through a big list to find a specific turtle.

**US9:** As a user I want to be able to filter the messages by type, so I e.g., only see errors or warnings.

**US10:** As a user, I want to be able to see how long a turtle has to wait before it starts a new run.


## C4-Model
### Level 1
![Context Model](https://github.com/Josian2004/s3-ip-portfolio/blob/main/portfolio_images/C4-MCST/C4-Model-C1.drawio.png)

This is the whole MCS Ecosystem, these are all MCS Services which the MCS team have built and this diagram shows how they are connected. The main connection is, of course, the Minecraft Server (MCS Server), this is where all of the data comes from and is sent. Furthermore, Vincent (MCS Analyser) and I (MCS Turtle Tracker) both use the MCS Systems API. This API provides data about all the systems in our server, e.g. you can request a list with all of the farms or request a specific farm. I use this information to sort the turtles by the system. 

We also have a portal website, on this portal are buttons to go to every service we have. We have an authentication system implemented on this portal which we are going to use in the future to lock specific features from my app so not every random person can control the turtles.

### Level 2
![Container Model](https://github.com/Josian2004/s3-ip-portfolio/blob/main/portfolio_images/C4-MCST/C4-Model-C2.drawio.png)

Now we are going to zoom in on my application and the directly connected services. In this diagram, you can specifically see what services are connected and how they communicate. It also shows that my app consists of a front-end web app, a back-end Java server and a MySQL database and that there are WebSocket connections between my front-end and back-end and MCS server and back-end.

## Projects
This project is actually working and deployed on my server so you can see it for yourself at:\
https://turtletracker.mcsynergy.nl

### [Front-end](https://git.fhict.nl/I483898/mcst-vue-frontend)
For the front-end web-based application I used Vue.js as my JavaScript framework, I chose Vue because of its component system, which makes the code more easily readable and gives me the option to easily reuse components in other parts of my web app without the need to rewrite it.
It’s also a lightweight framework which makes my app a lot more responsive and faster.\
Lastly, I have some very entry-level experience with Vue which isn’t enough to build a full web application, so I want to widen my Vue knowledge so that in the future I’m able to create a full Vue web app.\
For styling I use CSS and Tailwind, this is a styling library which makes it very easy and fast to create a good-looking webpage.\
Furthermore, I use an npm package called Axios. This package gives me the ability to easily create HTTP requests to the MCS Systems API (external API).

### [Back-end](https://git.fhict.nl/I483898/mcst-springboot-backend)
#### Logic
The back end consists of multiple microservices, each microservice contains two or three of these components:
-	Controller: Responsible for listening and responding to incoming requests.
-	Websocket Handlers: Responsible for listening for/sending messages over WebSocket.
-	Service: This is where all the logic for the specific microservice is.
-	Events: These are used for dependency inversion so that the service is independent of the e.g. WebSocket handlers.
-	Repository: Part of Spring Data JPA and responsible for communicating with the database.
-	Models: This is where all the data is stored and used across the microservice.

The microservices are built with the SpringBoot framework and thus are written in Java.
The reason I chose Java is that I’ve used C# last semester and I want to learn a different language.
I chose SpringBoot because it is one of the biggest and most popular Java frameworks so there is a lot of documentation available. It also has Dependency Injection which makes it very easy to create loosely coupled modules.

The back end is made of microservices, I chose these because:
1.	Improved scalability: It’s very easy to up or downgrade specific services or add a new service with a new feature without the need to dive deep into the code to change something. I can easily remove a service and the rest of the application should just continue to work.
2.	Future-proofed: If a technology updates, I can easily replace a whole microservice with something better without the need to change code in other parts of my application which makes it very easy to maintain the application and keep updating it with the latest technologies and innovations.
3.	Teamwork: This isn’t relevant to my individual project, but it is for the proftaak. With microservices, you can easily split up the work between different team members without interfering with each other code. So, no more annoying code merging problems.

#### Data Persistence
I'm using the ORM Spring Data JPA because it is build-in in Spring Boot, the ORM is responsible for retrieving/saving all the data from my application.
I'm using a MySQL database for storing the data.

### Resource Server
All my data is coming from the Minecraft server, it works as follows.\
All the turtles (robots) send their data (location, message, etc.) to a central system over a "Minecraft network". 
When this central system receives a message, it will send the message over a WebSocket connection to the backend server.\
The system uses ComputerCraft (Minecraft Mod) which has a built-in WebSocket en HTTP feature to establish a connection with my back-end server.\
All the scripts for this mod are written in Lua.

### [External API](https://docs.naamdorpboot.xyz/systems-api)
In our server, we have a lot of farms (systems as we call them) and most turtles are assigned to a specific farm. To get the information on all the farms currently active in the server, a friend of mine has written an API where we can request said data. This way my app will always have the latest farm data without the need to hard-code a newly build farm.

## Quality Assurance
### What is QA?
To make sure that my app works and performs as expected, I need to test everything. There are two different types of tests, functional and non-functional tests. 

With functional tests, you test if the code works as expected so that when I enter 2+2, the answer will actually be 4. If these tests fail then there is something very wrong in your code which will make your app not function properly.

Non-functional tests are there to test the quality of the code and app. It doesn't test if the app works as expected, but it is there to test how well the app works. Two examples are performance tests, to analyse load times and responsiveness, and UX tests, to see if your UI is user-friendly and nice to use as a user.
### Test Plan
At the moment of writing, I don't have any complex logic in my back-end services and this makes unit tests pretty useless for my application. However some parts I feel like do need to be tested with unit tests, so I'm going to write a few unit tests but my code probably won't get an 80% or higher code coverage. Things like a method to save something in a database aren't going to be tested by unit tests, these are tested with integration tests. The things I am going to test are exception handling and JSON conversions. With exception handling, I want to test that the correct exceptions are thrown when something happens that shouldn't and that those exceptions are correctly handled and not just thrown as a RuntimeException. I also want to test the conversion of JSON to Java object or the other way around, in the past, I've had some incorrect conversions so that's why I find it important to test this. However, I do find it important that I can easily add unit tests in the future because in I have some new features planned and they might contain some more complex logic which I do want to test with unit tests.

I do have a lot of components (units) which are dependent on each other and it is vital for the integrity of my app that the communication between these is tested and functional. For this I'm going to write integration tests, these tests are going to make sure that e.g. a computer or log is properly saved in the database or that the requested data is correctly returned. There won't be any mock objects or interfaces with integration tests so I will need some form of a database to test it all on. It is a very bad idea to use your production database for testing so I'm going to host a second database for testing purposes, this database will be wiped every time it is done testing so that it won't influence the next testing phase.

I'm going to carry out a UX survey with the MCS Players to see what they think about the current UI and UX and if they want to see things differently or if they find some aspects of the UI confusing. I will then of course implement the results in a new UI and run the survey again to see if the problems are resolved. Another tool I'm going to use to gain feedback is GitHub itself, MCS Players can open issues when they feel something needs to be different.

To improve the quality of my code, I'm going to implement a SolarQube codescan. This is a tool which will scan my code and create a report based on the results. It checks things like code coverage (how much % of my code is covered by unit tests) and duplicated code (the same code which is written in different places). It also generates a whole list of issues, these are things that I could improve in my code to better follow code standards and overall improve my code.

Performance is one of the most important aspects of a front-end application, a user will leave a website faster if the load times are slow and the site is not very responsive. To test this, I'm going to use Google Lighthouse. This is a tool which will test my whole website and generate a report with scores, the tested components are performance, accessibility, best practices, SEO and PWA. When the score of a component isn't at a 100%, Lighthouse will give tips on where to improve my code to get closer to that 100% score. It also checks if your website is PWA compatible, this is pretty useful for me because I have the intention to make my app installable on mobile devices.

### Implementation
#### Unit/Integration Tests
I've implemented integration tests and a few unit tests, the unit tests are only testing that the services actually update the information in the local storage instead of adding a new instance to it. All of my controllers are tested (by integration tests) by actually executing the methods in the controller so that every layer is tested. I've created a separate testing database where these tests can be run so that I'm not using any production data for testing and manipulating it. At the beginning of every test, all the data is removed from the database and mock data is added.

These are all the tests which are being run when a push is made to GitLab:
[<img src="https://github.com/Josian2004/s3-portfolio/blob/main/portfolio_images/passedIntTests.png" width="700"/>]([image.png](https://github.com/Josian2004/s3-portfolio/blob/main/portfolio_images/passedIntTests.png))
#### UX
I've done a UX research to improve the UX of my application. The content and results of this research can be found [[here]](https://github.com/Josian2004/s3-portfolio/blob/main/Research/UXResearch.md).
#### SonarQube
I've set up my own SonarQube server, every time a report is generated it will be uploaded to this server where I can then inspect the report. It will scan my code for coverage, duplications, bugs and vulnerabilities. As stated in my test plan, the coverage will probably stay low because I feel that unit tests are not very useful in my application.

This is an example of a report
![SonarQube Report](https://github.com/Josian2004/s3-portfolio/blob/main/portfolio_images/sonarqubereport2.png)

#### Google Lighthouse
A website must be fast and responsive, studies have shown that users often leave a site because it takes too long to load. To test this, I've implemented that when a commit is made, a Google Lighthouse report is automatically generated. In this report is a lot of useful data about load time, response times etc. and a lot of "Good practices" to optimise a website.

This is an example of a report:
![Lighthouse Report](https://github.com/Josian2004/s3-portfolio/blob/main/portfolio_images/lighthousereport1.png)

These reports are all uploaded to a self-hosted [Lighthouse CI Server](https://lighthouse.josian.nl) where you can easily see past reports and compare them to each other to see in what areas the website has improved. It will also generate a graph so you can see the improvement over time.
In the reports are also tips on how to improve the website even more with precise places where performance/load times can be gained.

## Continuous Integration and Deployment
To automate the test and deployment process of my application, I implemented a CI/CD pipeline for both my web app and server. This has been done with GitLab CI/CD.
To keep my data secure, I've made environment variables for all the sensitive data like passwords, keys etc. These pipelines are automatically triggered when a push is made to either the main branch or the development branch. However, only when pushed to the main branch will the app be built and deployed, when pushed to the development branch it will only run the tests.

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
What this file does is, firstly it will install an http-server so I can run the app. Then it will copy the *package.json* and install all the necessary packages for the application to build. Then it will copy the rest of the files and build the application, this will then create a /dist folder which the HTTP server uses to start the app.
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
This file does almost the same as the front-end file, however, it won't build the application. It will simply copy the .jar file and run it using Java.

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
This docker-compose file is a little bit different from the front-end file because this file starts two containers. It will also start a MySQL v5 container with a Docker Volume to make sure the data isn't lost when the container is stopped and removed.
Then it will start the back-end server with some environment variables and settings for the database connection.
Because the back-end server won't start/run without a database, I've specified that the server depends on the database.
Another nice feature is that because we have both containers in one file, it will also create a Docker network with both in it so the back-end can communicate with the database without using its external IP address. Technically I don't have to expose port 25002 for the database but I like to have the ability to see the contents of the database externally.

### Pipeline
#### Build Job
```yaml
build:
    stage: build
    image: eclipse-temurin:17-jdk-alpine
    before_script:
        - chmod +x mvnw
    script: "./mvnw install"
    artifacts:
        paths:
        - target
```
This job is responsible for building the application, it will run the *./mvnw install* command which will build the app into an executable .jar file and save the target folder so further jobs can use it.

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

```yaml
# Front-end pipeline only
lhci:
    stage: test
    image: cypress/browsers:node16.14.0-chrome99-ff97
    script:
        - npm install
        - npm install -g @lhci/cli@0.9.x
        - npm run build
        - lhci autorun

```
For my front-end pipeline, I have a job which automatically runs Google Lighthouse and generates a performance report. This report is then uploaded to my own [Lighthouse CI Server](https://lighthouse.josian.nl).
I could, if I wanted to, set up that if the site didn't perform well enough, the job would fail. However, this is useless in a development phase because nobody expects the site to perform at 100% and the job would probably fail every time.

```yaml
# Back-end pipeline only
sonarqube-check:
    stage: test
    image: 
        name: sonarsource/sonar-scanner-cli:latest
        entrypoint: [""]
    variables:
        SONAR_USER_HOME: "${CI_PROJECT_DIR}/.sonar"
        GIT_DEPTH: "0"
    cache:
        key: "${CI_JOB_NAME}"
        paths:
        - .sonar/cache
    script: 
        - sonar-scanner
    allow_failure: true
```
For my back-end pipeline, I have a job which automatically generates a SonarQube report and uploads it to my own SonarQube server. I also could make this job fail if the score wasn't at a certain level, however, because I don't intend on implementing very many unit tests it would fail every time.

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
This job is responsible for preparing my application to be deployed, it will first build the docker image with the correct environment variables and then push this image to a self-hosted Docker Registry. Because this is a secured registry, it will first need to log in using secret variables before it can push an image.

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
This is the final job and it's responsible for deploying the application to a server. Alpine Linux doesn't natively have an ssh-client installed so that is what I'm doing manually in the *before script*. Then I have to add my *SSH_PRIVATE_KEY* to the client so it can connect to my server using that key.\
It will then connect to my server over SSH and do a few things:
1. It will run *docker-compose down* which will stop and remove the old container.
2. It will log in to my Docker Registry.
3. It will pull the latest image which we pushed in the last job.
4. Finally it will run *docker-compose up -d* which will start a new container with the latest image.
And then my application is up and running again.

### Deployment Environment
Even though it is sufficient for this semester to "deploy" to the Docker Hub, I felt that it wasn't complete until me and my friends could access my app from wherever we are.

So in the autumn break of 2022, I bought an HP Workstation from Marktplaats and repurposed it as a home server. I deleted Windows and installed Ubuntu.\
Before I bought this server, I came across a few issues with my CI/CD. First of all, the Docker Hub only allows for one free private repository which isn't enough for both my web app and server so I would need to host my own registry somewhere. Second of all, Fontys doesn't have any shared GitLab-runners... So I needed to host these myself as well. And lastly, I needed a place to deploy my app with the possibility to expose it to the internet.

I now have a Docker Registry, two GitLab-Runners, a Lighthouse CI Server, a SonarQube server and of course my whole MCST Application running on my server and they are accessible via my domain josian.nl, I have also set up a [Nginx](https://www.nginx.com/) Reverse Proxy so I can use fancy sub-domains like mcst.josian.nl for my apps instead of ugly ports after my URLs. 
With the use of [LetsEncrypt](https://letsencrypt.org/) and [Certbot](https://certbot.eff.org/) I secured my applications with SSL certificates and HTTPS, which also gives me the possibility to build my app into a PWA.

I know this has nothing to do with my learning outcomes for this semester, but I've learned a lot of other skills like basic infrastructure and security while setting this up which I feel are also important as a software engineer and it was of course fun to do.

## Business processes

I've created two business processes for my application, one without my app and one with my app.

![business process before](https://github.com/Josian2004/s3-portfolio/blob/main/portfolio_images/BusinessProcess-Before.drawio.png)

There are a few problems with the current process. There is a big posibility that the player never notices that a turtle has crashed, this will result in the system staying inoperational. It could sometimes take days before someone comes across the system and sees that is isn't working anymore which isn't optimal. When someone does notice that something is wrong, they still need to search for the crashed turtle and they have no idea where this turtle could be. It can happen that the turtle got out of their designated space and is now walking somewhere where the player didn't even know was possible. This will result in a loose turtle and the player needing to replace it.

I've fixed these problems with my application like shown in the next business process.
![business process after](https://github.com/Josian2004/s3-portfolio/blob/main/portfolio_images/BusinessProcess-After.drawio.png)

Now when a turtle crashes, a message is send to the server and the server then sends it to the website. The player then sees the message and can quickly see that something went wrong, the message also contains the reason for the crash so the player can instantly start to fix it. If rebooting fixes the problem, the player can do that easily from the website so he doesn't have to enter the game and physically go to the turtle. If the issue isn't resolved by a reboot, the player can see the last known location of the turtle. If the turtle has gotten loose, the player can see where it has gone to so he doesn't have to search the whole area.


## Professional
During the semester, I've had multiple feedback conversations with Jean-Paul about the progress of my application and learning outcomes. I've documented the contents of these conversations in feedpulse, the next screenshot is one of those.

![Feedpulse Screenshot](https://github.com/Josian2004/s3-portfolio/blob/main/portfolio_images/feedpulseSs.png)

Furthermore I have presented some of our sprint deliveries at iO and we have repeatedly requested feedback from our product owners at iO and then implemented that feedback in our product. More about this is explained in the Agile learning outcome.

## Agile
### What is agile?
Agile is a project management style that focuses on flexibility, collaboration and customer satisfaction. This involves breaking projects into smaller, manageable chunks and working on them continuously with regular feedback and adjustments. It enables teams to respond quickly and efficiently to changes and challenges and deliver high-quality results on time. Agile, which emphasizes teamwork and open communication, is often used in software development, but can be applied to a wide variety of industries and projects. 

Some of the most commonly used agile methods are Scrum, Kanban and Extreme Programming (XP).

### What are the differences between Agile and Waterfall?
Agile and Waterfall are two different approaches to software development. With the waterfall approach, each phase of the project must be completed before moving on to the next phase. This shows that the requirements of the project are determined in advance and detailed plans are prepared before any work is carried out.

Agile, on the other hand, is a more adaptive and iterative approach to software development. Agile projects are planned and developed in short iteration cycles called "sprints" and project requirements are not predetermined. This allows the team to quickly respond to changing requirements and user feedback. The respective focus and flexibility of these two strategies ultimately differentiate them. Agile is more flexible and adaptable than the more organized and planned Waterfall. Each strategy has its advantages and is useful in different situations.

### Scrum
Scrum is a framework for project management and completion. It is based on the concept of self-organizing teams, which emphasizes collaboration, continuous improvement, and regular review and revision of project plans. In the Scrum method, projects are divided into manageable chunks called "sprints". Sprints typically last two to four weeks, and at the end of each sprint, the team must have a functional, shippable product. 

There are several important roles within Scrum, including the Scrum Master, who facilitates the process, and the Product Owner, who represents the stakeholders and organizes the work to be done. Team members are empowered to direct their own work and decisions and are responsible for the actual work being done. 

To discuss progress and identify any obstacles or issues that need to be resolved, the team holds daily stand-up meetings throughout the sprint. The team holds a review meeting at the end of the sprint to demonstrate new features and review what is working and what needs improvement. Flexible and adaptable, Scrum encourages teams to periodically review and revise their procedures to improve efficiency and effectiveness. 

One of the main advantages of using Scrum is its emphasis on continuous improvement.

### Kanban
Workflow control and improvement is done using Kanban. The focus is on visualizing work, limiting work in progress and continuously improving workflows. It is based on the principles of just-in-time production.

Kanban represents work using cards on a board, and the board is usually divided into columns to represent the stages of the work process. For example, a list of tasks for a software development team might display Tasks, In Progress, and Complete columns. As work is completed, the cards move from left to right, providing a visual representation of the workflow. 

Limiting work in process (WIP) is one of the core concepts of Kanban. Teams can prevent individual team members from becoming overwhelmed and reduce the potential for bottlenecks or delays by limiting the number of projects they are actively working on at any given time. 

Continuous improvement is one of the main principles of Kanban. Teams are encouraged to regularly evaluate work processes and look for opportunities to improve efficiency and effectiveness.

### Extreme Programming
A software development methodology called Extreme Programming (XP) emphasizes communication, clarity, and feedback. It focuses on frequent releases with short development cycles and facilitates collaboration between customers and developers throughout the project. With the XP approach, each team member is responsible for a specific area of the project. The team works compactly, self-organizing. A close working relationship and open, frequent communication is required between team members.

Frequent small releases are one of the founding principles of XP. Encourage the team to break the project into manageable chunks and release functional software as often as possible. To make necessary changes to the project plan, the team can do so by frequently soliciting feedback from users and stakeholders early in the project. Simplicity is another important XP principle. Encourage the group to create simple, clean code that is easy to read and maintain. This reduces the chance of errors and other problems and makes it easier for new team members to get up to speed.


### Agile in our project
We used Scrum in our project, we had split the project in 5 3 week sprints. We started the day with a stand-up and ended it with a stand-down so we constantly knew who were doing what part of the project. At the end of every sprint we would go to the office of iO Digital to present the results of the last sprint, we would show them a short demo of the then finished product and we would ask if they had any comments on the current project.

We would end the presentation with a plan for the next sprint, the stakeholders could then add or remove things from this plan to their liking. This way the stakeholder has direct impact on the userstories we will be working on in the next sprint and there would't be any surprises for them.

The Agile tool we eventually used was Jira, this way we could easily track the progress of our project and it was also the main form of communication with our stakeholders. Everytime we needed help or we had a question, we would ask it in a Jira ticket and then assign it to them so they knew we needed help and could then provide it. Because the stakeholders had access to the Jira board, they could see at any time the progress of the sprint and if we were on track to finish the agreed userstories. Jira also gave us the posibility to generate a burndown chart, this is a chart where you can easily see if you are on track. The more tickets you complete, the more the red line goes down and while the red line is under the gray line, you are on track.

![Jira Board](https://github.com/Josian2004/s3-portfolio/blob/main/portfolio_images/jiraboard1.png)

![Burndown](https://github.com/Josian2004/s3-portfolio/blob/main/portfolio_images/burndown1.png)
## Ethics
### What is ethics in software engineering?
In software development, ethics refers to the values and principles that guide the creation of software. Together, these principles and values aim to ensure responsible, fair, and transparent development and use of software. Typical ethical rules in software development are:

- Respect for users: This principle emphasizes the importance of taking into account the needs and interests of users when designing and developing software. This can mean that the software is user-friendly, accessible to people with disabilities, and secure to protect user data and privacy. 

- Responsibility: This principle emphasizes the importance of being responsible for the impact of software on individuals and society. This may include the potential risks and consequences of the software, as well as precautions to minimize any adverse effects. 

- Fairness: This principle emphasizes the value of fair and equitable treatment of all users. This may include ensuring that the software is accessible and usable by people of diverse backgrounds and abilities, and avoiding discrimination or bias in its development or use. 

- Transparency: This principle emphasizes the importance of being open and transparent about how software is designed and works. One way is to enable users to understand and manage their data usage by providing clear and accurate information about the software.

### Why is it important?
Because the software we develop has the potential to significantly impact people and society, ethics are paramount. As software engineers, the choices we make can have far-reaching consequences, from the security of our critical infrastructure to the privacy of our personal data. We can help ensure that software is used responsibly, fairly and transparently, while considering ethical principles and values in its design and development. This not only reduces the negative impact of software on people and society, but also helps protect the rights and interests of users. 

Furthermore, ethics are essential in software development because they help build trust in the technology we produce. As software becomes more and more integrated into our daily lives, people need to trust and rely on the software they use. Software developers can help build and maintain this trust through ethical behavior. They can also ensure that the technologies they develop are used in ways that benefit society.

### Ethics in our project
I have personally encountered ethics as well, it was a part of our group project. We have created an app that the employees of iO Digital can use to 'track' their colleagues. It happened too often that someone needed their colleague, he then searched the whole building just to find out that the colleague was working from home that day. To fix this, we have created an app where employees can see whether the person they are looking for is at the office or home. All the users are prompted to set where they are at the beginning of every day, if they don't specify the system uses the wifi logs of the iO building to see if their phone is connected and if this is the case, their status is automatically set to 'at office'.

To make this app as effective as possible, we need some sensitive personal data from its users like their full name, iO email address and some location data. To protect this data we were given an iO Legal Document that contained several measures to protect the privacy and data of the users and to make sure we weren't gathering any more data than was necessary. We also created some of our measures to protect the data which I will explain in the next few paragraphs.

As stated earlier, transparency is one of the most important principles in ethical software development. That's why we have made sure that every user always can see the terms and services of our app, the user will first be prompted with them when they are verifying their account and on the settings page, the user can also always view them.

Only iO employees must be allowed to access the app, originally we had the idea to use their own SSO to make sure that the user is an iO employee but we quickly heard that this wouldn't be possible in the short period of the project so we had to figure it out ourselves. We decided to use Google Login to authenticate users but we still had the problem that everyone with a Google account could just log in and use the app so we eventually came up with the idea to use the @iodigital.com email addresses to verify that the user was an iO employee. During the registration process, the user will be asked to fill in their @iodigital email, then our server would check if it was an iO Digital email and send them a verification email (as shown in the picture below).

![iO Verification Email](https://github.com/Josian2004/s3-portfolio/blob/main/portfolio_images/verificationmail.png)

Once verified, the user will be able to continue to the app and use it.

To make sure that not everyone can just request the data from our API, we have implemented a token-based authentication system. When the user logs in he will receive a JWT from Google which will be included in every API call, in the back-end we check if the JWT is valid and if that user is a verified iO Digital employee, if it is all valid, only then will the server return the requested data. This token will expire after an hour to prevent the token is stolen and used for unauthorized access.

The most sensitive data we use are the WiFi logs from the iO building, these contain MAC-Addresses, names and sometimes precise location data like the floor they are on. We will never directly save this data, we will only analyse it, and when that is done, delete it. The only thing we do save is if a MAC address from a user is detected at the office, we will save that. But when the data refreshes and that specific user isn't detected anymore, we will delete that status and there isn't any history saved. In conclusion, this means that the data is only saved when someone is actually at the office and when they leave, the data will be saved for a maximum of 15 minutes and then deleted.

To prevent data leaks, all of the servers are running in the AWS environment of iO. These environments have some severe security measures which are actively monitored by iO so if something might go wrong, they will instantly see it and prevent any data leaks.


## Cultural Differences
### What are cultural differences?
Cultural differences refer to the ways in which different cultures around the world have unique customs, beliefs, and ways of life. These differences can include things like language, dress, food, music, art, and religious practices. Cultural differences can also refer to the ways in which people from different cultures communicate, think, and view the world around them.

### Why is it important in Software Development?
Cultural differences can play a role in software development in a number of ways. For example, people from different cultures may have different communication styles, which can affect how they work together on a team. They may also have different ideas about what constitutes good design or how to prioritize tasks. In some cases, cultural differences can lead to misunderstandings or conflicts within the team.

To address these issues, it's important for team members to be aware of and respect each other's cultural backgrounds. This can involve things like learning about each other's communication styles and working to find common ground. It can also involve being open to different perspectives and finding ways to incorporate different ideas into the project.

Overall, cultural diversity can be a strength in software development, as it can bring a variety of perspectives and experiences to the table. By working together and respecting each other's cultural differences, teams can create high-quality software that meets the needs of a diverse user base.

### Hofstede's Cultural Dimensions
This is a cross-cultural communication framework developed by Geert Hofstede, it can be used to see the effects of a society's culture on the values of its members and how these relate to behavior. It consists of six dimensions as explained below. He scored each country on a scale of 0 to 100 for each dimension.
#### Power Distance Index
This is a reference to the level of inequality that exists between those in positions of power and those who do not. A high score means that there is a large inequality in the distribution of power which society accepts, people understand "their place" in the system. While a low score is the opposite, power is shared and society does not accept situations where power is divided unequally. 

#### Individualism versus Collectivism

#### Masculinity versus Femininity

#### Uncertainty Avoidance Index

#### Long- versus Short-Termn Orientation

#### Indulgence versus Restraint

# Sources
- Agile Alliance. (2022, 15 december). What is Agile? | Agile 101 | Agile Alliance. Agile Alliance |. https://www.agilealliance.org/agile101/
- What is Agile? And when to use it. (z.d.). https://www.coursera.org/articles/what-is-agile-a-beginners-guide
- Trapani, K. (2022, 21 november). What is Agile and What is Scrum? Cprime. https://www.cprime.com/resources/what-is-agile-what-is-scrum/
- Denning, S. (2016, 13 augustus). What Is Agile? Forbes. https://www.forbes.com/sites/stevedenning/2016/08/13/what-is-agile/?sh=4c83a53a26e3
- What is Scrum? (z.d.). Scrum.org. https://www.scrum.org/resources/what-is-scrum
- Lutkevich, B. (2021, 28 oktober). Scrum. Software Quality. https://www.techtarget.com/searchsoftwarequality/definition/Scrum
- Waterfall Methodology: A Complete Guide. (2022, 18 maart). https://business.adobe.com/blog/basics/waterfall
- Gantt Chart Software. (2022, 15 december). ProjectManager. https://www.projectmanager.com/guides/waterfall-methodology
- What Is Kanban? Explained in 10 Minutes | Kanbanize. (z.d.). Kanban Software for Agile Project Management. https://kanbanize.com/kanban-resources/getting-started/what-is-kanban
- Atlassian. (z.d.). What is Agile? https://www.atlassian.com/agile
- https:\/\/www.agilealliance.org\/author\/12#author. (2021, 11 maart). What is Extreme Programming (XP)? | Agile Alliance. Agile Alliance |. https://www.agilealliance.org/glossary/xp/
- MindTools | Home. (z.d.). https://www.mindtools.com/a1ecvyx/hofstedes-cultural-dimensions
- Wikipedia contributors. (2022, 27 december). Hofstede’s cultural dimensions theory. Wikipedia. https://en.wikipedia.org/wiki/Hofstede's_cultural_dimensions_theory
- Burak, A. (2021, 3 november). 6 Best Practices to Overcome Cultural Differences in Offshore Software Development. Relevant Software. https://relevant.software/blog/6-best-practices-to-overcome-cultural-differences-in-offshore-software-development/
