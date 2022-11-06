# Individual Project

## Table of Contents
- [NS-Tracker](#ns-tracker)
  - [Project description](#project-description)
  - [Requirements](#requirements)
  - [C4-Model](#c4-model)
    - [Level 2](#level-2)
    - [Level 3](#level-3)
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
### Level 3
## Technology Stack
### Front-end Stack
### Back-end Stack
## Conslusion
# MCSTurtleTracker
## What is MCS?
## Project Description
## Requirements
## User-stories
## C4-Model
### Level 1
### Level 2
## Projects
### Front-end
### Back-end
### Resource Server
### External API
## Software Quality
## Continuous Integration and Deployment
### Pipeline
### Deployment Environment
