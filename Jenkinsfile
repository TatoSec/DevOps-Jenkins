pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
               checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/TatoSec/DevOps-Jenkins.git']])
            }
        }
        stage('Changing Directory') {
            steps {
               dir('/var/jenkins_home/workspace/Pipeline-Main/my-app') {
    // some block
}
            }
        }
        stage('Launch React App') {
            steps {
               sh 'npm start'
            }
        }
    
    }
}
