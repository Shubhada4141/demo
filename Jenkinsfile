pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Getting Utility App code from GitHub'
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                echo 'Building Docker image'
                bat 'docker build -t utility-app:latest .'
            }
        }

        stage('Run Docker Container') {
            steps {
                echo 'Running Utility App container'
                bat 'docker stop utility-app-container || exit 0'
                bat 'docker rm utility-app-container || exit 0'
                bat 'docker run -d -p 8000:8080 --name utility-app-container utility-app:latest'
            }
        }
    }
}
