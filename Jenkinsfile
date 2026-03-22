pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/JiyanneKateTuazon/COMP367_DevOps_Lab3.git'
            }
        }

        stage('Build WAR File') {
            steps {
                bat 'mvn clean package'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t lab3app .'
            }
        }

        stage('Run Docker Container') {
            steps {
                bat 'docker stop lab3app-container || exit 0'
                bat 'docker rm lab3app-container || exit 0'
                bat 'docker run -d -p 8081:8080 --name lab3app-container lab3app'
            }
        }
    }
}