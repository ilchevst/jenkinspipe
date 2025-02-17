pipeline {
    agent any

    environment {
        DOCKERHUB_CREDENTIALS = creddentials('ilchevst-dockerhub')
    }
    stages {
        stage('Build') {
            steps {
                sh 'docker build -t ilchevst/dp-alpine:latest .'
            }
        }
        stage('Login') {
            steps {
                sh 'echo $DOCKERHUB_CREDENTILAS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('Push') {
            steps {
                sh 'docker push ilchevst/dp-alpine:latest'
            }
        }
    }
}