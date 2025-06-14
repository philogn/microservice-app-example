pipeline {
    agent any

    stages {
        stage('Preparation') {
            steps {
                git url: "https://github.com/philogn/microservice-app-example.git", branch: 'main'
            }
        }

        stage('Build') {
            steps {
                echo 'Building...'
                // Simulate build process
                sh 'docker-compose build'
            }
        }

        stage('Trivy FS Scan') {
            steps {
                sh 'trivy fs --exit-code 0 --severity MEDIUM,HIGH,CRITICAL .'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                def scannerHome = tool 'sonar-scanner' 
                withSonarQubeEnv() {
                    sh 'sonar-scanner'
                }
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
