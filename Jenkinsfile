pipeline {
    agent any
    
    options {
        // Keep only the last 10 builds
        buildDiscarder(logRotator(numToKeepStr: '10'))
        // Timeout after 10 minutes
        timeout(time: 10, unit: 'MINUTES')
    }
    
    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out code from repository...'
                checkout scm
            }
        }
        
        stage('Build') {
            steps {
                echo 'Building the project...'
                
            }
        }
        
        stage('Test') {
            steps {
                echo 'Running tests...'
                
            }
        }
        
        stage('Archive') {
            steps {
                echo 'Archiving build artifacts...'
                
            }
        }
    }
    
    post {
        always {
            echo 'Pipeline completed. Cleaning up...'
        
            cleanWs()
        }
        success {
            echo 'Pipeline succeeded! ✅'
        }
        failure {
            echo 'Pipeline failed! ❌'
        }
    }
}