pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Compile') {
            steps {
                sh "${tool('Maven3')}/bin/mvn clean compile -DskipTests"
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    sh "${tool('sonar-scanner')}/bin/sonar-scanner -Dsonar.projectKey=simple-docker-webapp -Dsonar.sources=. -Dsonar.host.url=http://3.106.115.248:9000 -Dsonar.java.binaries=target/classes"
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
