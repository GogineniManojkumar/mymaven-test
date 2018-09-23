pipeline {
    agent any
    tools {
        maven 'LocalMaven'
    }
    stages {
        stage('pp-validate-compile') {
            steps {
                sh 'mvn clean validate compile'
            }
        }
        stage('pp-code-testing'){
            steps{
                sh 'mvn clean test'
            }
        }
        stage('pp-check-code-quality'){
            steps{
                sh 'mvn clean checkstyle:checkstyle'
            }
        }
        stage('pp-build-package'){
            steps{
                sh 'mvn clean package'
            }
            post {
                success {
                    archiveArtifacts artifacts: '**/*.war', fingerprint: true
                }
            }
        }
    }
}