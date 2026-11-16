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

        
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t simple-docker-webapp .'
            }
        }
    }
}
