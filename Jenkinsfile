pipeline {
    agent any
    tools {
        maven 'Maven3'
        jdk 'JDK21'
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/vinayk2499/simple-docker-webapp.git'
            }
        }
        stage('Build & Test (Maven)') {
            steps {
                sh 'mvn clean verify'
            }
            post {
                always {
                    junit testResults: 'target/surefire-reports/*.xml', allowEmptyResults: true
                }
            }
        }
    }
    post {
        success {
            echo 'Build SUCCESS - Maven build passed!'
        }
        failure {
            echo 'Pipeline failed - check console output above.'
        }
    }
}
