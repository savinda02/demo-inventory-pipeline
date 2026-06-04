pipeline {
    agent any
    stages {
        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t demo-inventory:latest .'
            }
        }
        stage('Deploy Application') {
            steps {
                sh '''
                    docker stop inventory-app || true
                    docker rm inventory-app || true
                    docker run -d -p 8081:80 --name inventory-app demo-inventory:latest
                '''
            }
        }
    }
}
