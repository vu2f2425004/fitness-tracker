pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/vu2f2425004/fitness-tracker.git'
            }
        }
        stage('Install Dependencies') {
            steps {
                sh 'pip install -r requirements.txt'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t fitness-app .'
            }
        }
        stage('Deploy Container') {
            steps {
                sh 'docker stop fitness-container || true'
                sh 'docker rm fitness-container || true'
                sh 'docker run -d -p 5000:5000 --name fitness-container fitness-app'
            }
        }
    }
}