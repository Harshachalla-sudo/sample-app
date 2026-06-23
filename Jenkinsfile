pipeline {
    agent any

    environment {
        IMAGE_NAME = "flask-demo"
    }

    stages {

        stage('Clone') {
            steps {
                git 'https://github.com/Harshachalla-sudo/sample-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t %IMAGE_NAME% .'
            }
        }

        stage('Run Tests') {
            steps {
                echo 'Running Tests...'
            }
        }

        stage('Deploy') {
            steps {
                bat '''
                docker stop flask-demo-container || exit 0
                docker rm flask-demo-container || exit 0

                docker run -d --name flask-demo-container -p 5000:5000 flask-demo
                '''
            }
        }
    }
}
