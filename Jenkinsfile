pipeline {
    agent any

    stages {
       stage('Docker build') {
            steps {
                sh '''
                docker version
                docker build -t node-backend .
                '''
            }
        }
    }
}
