pipeline {
    agent any

    stages {
        stage('checkout git') {
            checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/palash150403/Jenkins-docker-task.git']])
        }
    }
}