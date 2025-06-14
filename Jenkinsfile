pipeline {
    agent any

    stages {
        stage('Preparation') {
            steps {
                git url: "https://github.com/philogn/microservice-app-example.git", branch: 'master'
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
                sh 'trivy fs --exit-code 0 --severity MEDIUM,HIGH,CRITICAL . > trivy_report.txt 2>&1'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                script {
                    echo "Starting SonarQube analysis..."
                    def scannerHome = tool 'SonarScanner' 
                    withSonarQubeEnv("SonarQube") {
                    sh "echo Using scanner at: ${scannerHome}"
                    sh "${scannerHome}/bin/sonar-scanner -Dsonar.login=sqb_8d04a60a67fd9befe3151c5331a92461e2b6edfc"
                    }
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
