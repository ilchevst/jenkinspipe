pipeline {
    agent any

    environment {
        DOCKERHUB_CREDENTIALS = creddentials('ilchevst-dockerhub')
    }
    stages {
        stage('gitclone') {
            steps {
                git 'https://github.com/ilchevst/jenkinspipe.git'
            }
        }
        stage('Build') {
            steps {
                sh 'docker build -t ilchevst/dp-alpine:latest .'
            }
        }
        stage('Login') {
            steps {
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('Push') {
            steps {
                sh 'docker push ilchevst/dp-alpine:latest'
            }
        }
    }
    post {
        always {
            sh 'docker logout'
        }
    }
}