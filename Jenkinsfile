pipeline {
    agent any

    environment {
        DOCKER_HUB_REPO = 'bhawya17' 
        IMAGE_NAME = 'flask-jenkins-demo'
        IMAGE_TAG = 'latest'
    }

    stages {
        stage('Build Docker Image') {
            steps {
                echo "Building Docker image: ${DOCKER_HUB_REPO}/${IMAGE_NAME}:${IMAGE_TAG}"
                bat "docker build -t %DOCKER_HUB_REPO%/%IMAGE_NAME%:%IMAGE_TAG% ."
            }
        }

        stage('Login to DockerHub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub-creds', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
                    echo "Logging in to DockerHub..."
                    bat "docker login -u %DOCKER_USER% -p %DOCKER_PASS%"
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                echo "Pushing Docker image..."
                bat "docker push %DOCKER_HUB_REPO%/%IMAGE_NAME%:%IMAGE_TAG%"
            }
        }
    }

    post {
        success {
            echo '✅ Build and push completed successfully.'
        }
        failure {
            echo '❌ Build failed. Check the logs for details.'
        }
    }
}
