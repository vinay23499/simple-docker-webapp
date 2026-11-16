pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    sh "${tool('sonar-scanner')}/bin/sonar-scanner -Dsonar.projectKey=simple-docker-webapp -Dsonar.sources=. -Dsonar.host.url=http://3.106.115.248:9000"
                }
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t simple-docker-webapp .'
            }
        }
    }
}
