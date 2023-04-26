pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], userRemoteConfigs: [[url: 'https://github.com/DrobiDS/DevOps-project']]])
            }
        }
        stage('Build and Push Docker Image') {
            steps {
                sh 'docker-compose down'
                sh 'docker-compose build'
                sh 'docker-compose up -d'
            }
        }
    }
    post {
        success {
            echo 'Build successful!'
        }
    }
}
