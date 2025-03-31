pipeline {
    agent any

    environment {
        DOCKER_HUB_CREDENTIALS = credentials('docker-hub')
    }

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/deviprasannakakaraparthi/cicd-web-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t cicd-web-app .'
            }
        }

        stage('Login to Docker Hub') {
            steps {
                sh 'echo $DOCKER_HUB_CREDENTIALS_PSW | docker login -u $DOCKER_HUB_CREDENTIALS_USR --password-stdin'
            }
        }

        stage('Push Image to Docker Hub') {
            steps {
                sh 'docker tag cicd-web-app prasannakakaraparthi2303/cicd-web-app:latest'
                sh 'docker push prasannakakaraparthi2303/cicd-web-app:latest'
            }
        }
    }
}

