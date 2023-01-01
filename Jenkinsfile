pipeline {
    agent any

    stages {
        stage('Github Checkout') {
            steps {
               checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/TatoSec/DevOps-Jenkins.git']])
            }
        }
        stage('Changing Directory') {
            steps {
               dir('/var/jenkins_home/workspace/Pipeline-Main/my-app') {
   
}
            }
        }
        stage('Launching App') {
            steps {
               dir('/var/jenkins_home/workspace/Pipeline-Main/my-app') {
                   timeout(activity: true, time: 59, unit: 'SECONDS') {
    sh 'npm start'
}
               }
   

            }
        }
        
    }
}
