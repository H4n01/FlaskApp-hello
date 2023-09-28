pipeline {
    agent any
    stages {
        stage('Git Checkout') {
            steps {
                script {
                    git branch: 'main',
                        credentialsId: 'h4n01/******',
                        url: 'https://github.com/H4n01/FlaskApp-hello.git'
                }
            }
        }
        stage('DELETE CONTAINER') {
            steps {
                sh 'docker rm flask-app --force'
            }
        }
        stage('DELETE IMAGE') {
            steps {
                sh 'docker rmi flask-app:latest'
            }
        }
        stage('BUILD IMAGE') {
            steps {
                sh 'docker build -t flask-app .'
            }
        }
        stage('RUN CONTAINER') {
            steps {
                sh 'docker run -itd --name flask-app -p 80:5000 flask-app:latest'
            }
        }
    }
}
