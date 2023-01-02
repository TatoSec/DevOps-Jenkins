# Jenkins CI/CD Pipeline
## ⚠️Documentation in Development⚠️
[![N|Solid](https://cldup.com/dTxpPi9lDf.thumb.png)](https://nodesource.com/products/nsolid)
<img src="my-app\public\CI_CD diagram.drawio.png"></img>




>This Documentation shows the steps taken to create a Jenkins Pipeline, and an explanation of how all the tools used work hand in hand, and the functions they provide.


## Docker

* Install Docker on your local machine.
* Run this command to deploy the Docker Container: : `docker run -p  -p 50000:50000 -p 3000:3000 -p 8080:8080 -v jenkins_home:/var/jenkins_home jenkins/jenkins:lts-jdk11` the -p flag is used to expose ports to our network
* Write down the password that's created for you during this first time set up process: like `8458e513eacd41d8875ca3253f47d3a0`
* Go to `localhost:<8080>` and you should be prompted for this password 
* While the docker container is running, run cmd: `docker ps` to see what containers are running - copy the container ID for Jenkins, like `8f7c957e19fd`
* Run command: `docker exec -it -u 0 8f7c957e19fd /bin/bash` to open an interactive bash terminal within the Docker Container as root (user 0) 

## Jenkins
* Make sure your Docker container is running, Jenkins uses the container as an environment
* Once you have logged into Jenkins you will need to create a job
* Name the project as you wish and select Pipeline for the job
* The Pipeline should now be created select it and click ⚙️ Configure
* Copy the "Jenkinsfile" raw contents into the Pipeline Script section

## Explaining the Pipeline

> lets break down the pipelines "stages" step by step. First we must understand a stage is simply  a name for an operation a pipeline performs, and steps defines what this function will do. 

> Step 1-Github checkout : "checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/TatoSec/DevOps-Jenkins.git']])" calls upon my repository and does a checkout to establish a connection

> Step 2-Changing Directory: " dir('/var/jenkins_home/workspace/Pipeline-Main/my-app') " This changes directories within the Docker container, in this case we changed directories as our React App is within the "/my-app/" directory. This directly translates to " cd  .../Pipeline-Main/my-app "

> Step 3-Launching App: " timeout(activity: true, time: 60, unit: 'SECONDS') {
    sh 'npm start'} " We are creating a time out as we want the server to run for only a minute before it shuts down otherwise this stage would run indefinitely. As for "sh "npm start"" this is the script needed to initiate the web app.
    *Note: the 'sh' prefix allows us to run commands within our environment just as a user would. e.g 'sh "cat <filename>" ' would concatanate a file.





### License

MIT




