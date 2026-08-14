pipeline {

    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t devops-html-demo:latest .'
            }
        }

        stage('Run Container') {
            steps {
                bat 'docker stop devops-html-demo || exit 0'
                bat 'docker rm devops-html-demo || exit 0'
                bat 'docker run -d -p 8080:80 --name devops-html-demo devops-html-demo:latest'
            }
        }

        stage('Verify') {
            steps {
                bat 'curl http://localhost:8080'
            }
        }
    }
}