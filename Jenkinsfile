pipeline {
    agent any
    tools {
        maven 'Maven3'
        jdk 'JDK21'
    }
    stages {
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
