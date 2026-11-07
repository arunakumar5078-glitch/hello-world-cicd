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
                bat 'docker build -t hello-world-cicd:latest .'
            }
        }

        stage('Deploy Application') {
            steps {
                bat 'docker rm -f hello-world-cicd 2>NUL || exit /b 0'
                bat 'docker run -d --name hello-world-cicd -p 8081:80 hello-world-cicd:latest'
            }
        }
    }

    post {
        success {
            echo 'Hello World application deployed successfully!'
        }
    }
}