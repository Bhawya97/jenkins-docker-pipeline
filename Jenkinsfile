pipeline {
    agent any

    environment {
        IMAGE_NAME = 'flask-jenkins-demo'
        IMAGE_TAG = 'latest'
        DOCKER_HUB_REPO = 'your-dockerhub-username'
    }

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/your-username/jenkins-docker-pipeline.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $DOCKER_HUB_REPO/$IMAGE_NAME:$IMAGE_TAG .'
            }
        }

        stage('Login to DockerHub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub-creds', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
                    sh 'echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin'
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                sh 'docker push $DOCKER_HUB_REPO/$IMAGE_NAME:$IMAGE_TAG'
            }
        }
    }

    post {
        success {
            echo '✅ Image pushed to DockerHub successfully!'
        }
        failure {
            echo '❌ Build failed. Check logs.'
        }
    }
}
