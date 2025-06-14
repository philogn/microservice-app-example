pipeline {
    agent any

    stages {
        stage('Preparation') {
            steps {
                echo 'Preparing...'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building...'
                // Simulate build process
                sh 'echo Compiling source code...'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing...'
                // Simulate test process
                sh 'echo Running unit tests...'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying...'
                // Simulate deploy process
                sh 'echo Deploying to environment...'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully.'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}
