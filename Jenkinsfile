pipeline {
    agent any

    stages {
       stage('Docker build') {
            agent {
                docker {
                    image 'docker:24.0.5-dind'
                    args '-v /var/run/docker.sock:/var/run/docker.sock'
                }
            }
            steps {
                sh '''
                docker version
                docker build -t node-backend .
                '''
            }
        }
    }
}
