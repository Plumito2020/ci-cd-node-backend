pipeline {
    agent any

    environment {
        IMAGE_NAME = "zakazz571/backend-server"
        DOCKERHUB_CREDENTIALS = 'dockerhub_id'
    }

    stages {
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME .'
            }
        }
        stage('Login to Docker Hub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub_id', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
                    sh 'echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin'
                }
            }
        }
        stage('Push Docker Image') {
            steps {
                sh 'docker push $IMAGE_NAME'
            }
        }
        stage('Clean up') {
            steps {
                sh 'docker rmi $IMAGE_NAME || true'
            }
        }
    }
}
