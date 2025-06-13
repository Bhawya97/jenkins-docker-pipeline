pipeline {
    agent any

    environment {
        IMAGE_NAME = 'flask-jenkins-demo'
        IMAGE_TAG = 'latest'
        DOCKER_HUB_REPO = 'bhawya17'
    }

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/Bhawya97/jenkins-docker-pipeline.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t $DOCKER_HUB_REPO/$IMAGE_NAME:$IMAGE_TAG .'
            }
        }

        stage('Login to DockerHub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub-creds', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
                    bat 'echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin'
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                bat 'docker push $DOCKER_HUB_REPO/$IMAGE_NAME:$IMAGE_TAG'
            }
        }
    }

    post {
        success {
            bat '✅ Image pushed to DockerHub successfully!'
        }
        failure {
            bat '❌ Build failed. Check logs.'
        }
    }
}
