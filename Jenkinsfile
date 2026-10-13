
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Application') {
            steps {
                bat 'mvnw.cmd clean package -DskipTests'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t student-task-manager:latest .'
            }
        }

        stage('Verify Docker Image') {
            steps {
                bat 'docker images student-task-manager'
            }
        }
    }

    post {
        success {
            echo 'Student Task Manager pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check the console output.'
        }
    }
}
