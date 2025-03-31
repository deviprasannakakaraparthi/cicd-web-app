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
        withCredentials([usernamePassword(credentialsId: 'docker-hub', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
            sh 'echo "$DOCKER_PASS" | docker login -u "$DOCKER_USER" --password-stdin'
        }
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

