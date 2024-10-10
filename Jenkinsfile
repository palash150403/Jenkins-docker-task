pipeline {
    agent any

    environment {
        dockerImage = ''
        registry = 'palash150403/dockerjenkins'
    }

    stages {
        stage('checkout git') {
            steps {
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/palash150403/Jenkins-docker-task.git']])
            }
        }

        stage('Build docker image') {
            steps {
                script {
                    dockerImage = docker.build registry
                }
            }
        }
    }
}