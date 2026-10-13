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
                sh 'chmod +x mvnw'
                sh './mvnw clean package'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t student-task-manager:latest .'
            }
        }

        stage('Verify Kubernetes') {
            steps {
                sh 'kubectl get deployments'
                sh 'kubectl get pods'
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
