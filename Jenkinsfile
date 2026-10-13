
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build with Maven') {
            steps {
                bat 'mvnw.cmd clean package'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t student-task-manager:latest .'
            }
        }

        stage('Verify Kubernetes') {
            steps {
                bat 'kubectl get deployments'
                bat 'kubectl get pods'
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
