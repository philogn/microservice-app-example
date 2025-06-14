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
                    sh "${scannerHome}/bin/sonar-scanner -Dsonar.login=squ_087517a319a0833bf9a701614b10fac3eead3b6f"
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
