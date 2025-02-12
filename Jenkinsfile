pipeline {
    agent any
    tools {
        maven 'sonarmaven'
    }
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Aravind011464/maven-cicd'
            }
        }
        stage('Clean') {
            steps {
                sh 'mvn clean'
            }
        }
        stage('Compile') {
            steps {
                sh 'mvn compile'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
    }
    post {
        always {
            archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true
            junit 'target/surefire-reports/*.xml'
        }
    }
}
