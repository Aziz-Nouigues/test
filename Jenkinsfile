pipeline {
    agent any

    environment {
        SONARQUBE_SERVER = 'MySonar'
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Aziz-Nouigues/test.git'
            }
        }

        stage('Install dependencies') {
            steps {
                sh 'pip install -r requirements.txt'
            }
        }

        stage('Run tests') {
            steps {
                sh 'pytest'
            }
        }

        stage('SonarQube analysis') {
            steps {
                withSonarQubeEnv("${SONARQUBE_SERVER}") {
                    sh 'sonar-scanner'
                }
            }
        }
    }
}
