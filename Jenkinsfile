pipeline {
    agent any

    environment {
        dockerImage = ''
        registry = 'palash150403/dockerjenkins'
        registryCredential = 'f8c00948-9f27-404e-a459-e8c614695809'
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

        stage('Upload docker image') {
            steps {
                script {
                    docker.withRegistry( '', registryCredential ) {
                        dockerImage.push()
                    }
                }
            }
        }

        stage('Run conatiner') {
            steps {
                script {
                    dockerImage.run('-d -p 8086:80')
                }
            }
        }
    }
}