﻿[**React**](https://reactjs.org) is a JavaScript library to create interactive user interfaces. The core library is focussed on the view layer. It is declarative and component based. This quickstart uses [**create-react-app**](https://github.com/facebook/create-react-app) to scaffold a react app with no build configuration.


# Google Drive Clone using Hasura with Python Flask & ReactJS

This Readme list the steps to setup the codebase for both Python Flask backend and ReactJS front-end as microservices and build a GDrive(Google Drive) Clone - what we call as Hasura Drive.

The codebase makes use of the Hasura boilerplate templates of hello-Python-flask and hello-react to build a Drive Clone. The UI interface of the "Hasura Drive" mimic the GDrive.

## Hasura Drive supports limited Frontend features/tasks
- Users will be able to sign up/login as a user. The login is initiated by clicking on the profile picture icon on the top RHS cordner of the screen. If its a new user, you should choose to "SIGN UP" so that the account is created in the drive database.
![drive-login](https://user-images.githubusercontent.com/31035012/36072175-26331516-0f41-11e8-914b-c8542a4ac1ef.jpg)

The embedded video below shows how to sign up to use the drive:
[![Sign up video](https://img.youtube.com/vi/kkk-v8QuiJo/0.jpg)](https://www.youtube.com/watch?v=kkk-v8QuiJo)

- Users will be able to see/browse list of folders in their drive account
- Users will be able to upload/download files to/from their drive store
- Users will be able to view their recent 4 activities of the previous day in Quick Access section
- Users will be able view their activity for the drive on the Activity Slide Bar by clicking on (i) icon - "View details" on Top Right hand App bar


## Backend features implemented using Hasura API with Python Flask
- Schema modelling and Data Layer - using Data API
- Hasura services - Hasura Auth APIs for Login and Signup
- Custom services to support - File APIs on Hasura lets users upload and store files
- Data API to support - Tracking of User transactions like file upload, folder creation, user activity logging and activity review

## What all does the app support
- User can sign-up for a new account for the drive
- User can upload files to the drive (currently supported file extensions - 'txt', 'pdf', 'png', 'jpg', 'jpeg', 'gif','docx','xlsx','pptx','md')
- User can download the files to his local computer
- Users will be able to view their recent 4 activities of the previous day in Quick Access section
- Users will be able view their activity for the drive on the Activity Slide Bar

## What does this come with?
* React.js and Python Flask templates along with Drive Clone App Integration with ReactJS and Python Flask
  * Automatic reloading and bundling
  * All *create-react-app* feature
  * react-scripts with inbuilt webpack bundling
* Deployed with the [**serve**](https://www.npmjs.com/package/serve) package
* **Dockerfile** (automatically used by Hasura for deployment)


```
FROM node:8

RUN apt-get update && apt-get install -y build-essential python

#Install deps
RUN mkdir /app
COPY app/package.json /app/package.json
RUN cd /app && npm install
RUN npm -g install serve

#Add all source code
ADD app /app/
RUN cd /app && npm run build

WORKDIR /app

#Default command
CMD ["serve", "-s", "build", "-p", "8080"]
```

## Deployment instructions

### Basic deployment:

* Press the **Clone & Deploy** button and follow the instructions.
* The `hasura quickstart marianps/G-Drive-Clone` command clones the project repository to your local computer, and also creates a **free Hasura cluster**, where the project will be hosted for free.
* A git remote (called hasura) is created and initialized with your project directory.
* Now get your cluster name using `hasura cluster status` and modify the package.json file inside `microservices/mymicroservice/app/package.json`. Assign your cluster name to `REACT_APP_CLUSTER_NAME` environment variable.(in the example, it will be called "animator94", so you have to replace that name with your own cluster name).
* Run `git add .`, `git commit`, and `git push hasura master`.
* Run the below command to open your shiny new deployed react app.
``` shell
$ hasura microservice open mymicroservice
```
### DataSetup and DataEntry for quick use 

* On Browser type `https://app.<clustername>.hasura-app.io/index` for Data Entry login Service (Python-Flask Microservice) to open, You can use the same user that you have already created and else create a new user through Register link.
* Once you login, a homepage displayed where you can do the following:
  * Upload Files quickly
  * Create Folders quickly
  * Browse into Folders and create subfolders and upload files
  * This page is also to troubleshoot the api service extended from Python-Flask microservice.
* Logout once your dataset up is complete.
* Now login from microservice ui to use the drive
  * Note : Use the DataSetup and DataEntry only for purpose of Smoke testing and Sanity testing on App Drive Clone.

### Making changes and deploying

* To make changes to the project, browse to `/microservices/mymicroservice/app/src` for React JS part  and `/microservices/app/src/server.py` for the Python-Flask backend part.
* Commit the changes, and perform `git push hasura master` to deploy the changes.

## Local development

To test and make changes to this app locally, follow the below instructions.
* Open Terminal and `cd` into the project folder
* Run `npm install` to install all the project dependencies
* Run `npm start` and `npm build` in the terminal to build and run it.
* Make changes to the app, and see the changes in the browser

## View server logs

You can view the logs emitted by the ‘serve’ package by running the below command:

``` shell
$ hasura microservice logs mymicroservice
```
You can see the logs in your terminal, press `CTRL + C` to stop logging.

## Managing app dependencies

* System dependencies, like changing the web-server can be made in the Dockerfile
* npm/yarn deps can be managed by editing **package.json**.

If changes have been done to the dependencies, `git commit`, and perform `git push hasura master` to deploy the changes.

## Adding backend features

To make changes to backend features, you should refer to README-Base.md file in the repository

For further details, contact:
viju99@gmail.com
pritham.saldanha@gmail.com
shivguru06@gmail.com

## Contributions

* Vijaysankar - viju99@gmail.com - 
* Shiva Shankari G - shivguru06@gmail.com -  https://www.linkedin.com/in/shiva-shankari-g
* Marian P Saldanha - pritham.saldanha@gmail.com - https://www.linkedin.com/in/marian-p-saldanha-5957143
