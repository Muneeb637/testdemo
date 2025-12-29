pipeline {
    agent any
    
    environment {
        // Build information
        BUILD_NUMBER = "${env.BUILD_NUMBER}"
        BUILD_ID = "${env.BUILD_ID}"
        BUILD_TIMESTAMP = "${new Date().format('yyyy-MM-dd HH:mm:ss')}"
        
        // Workspace information
        WORKSPACE_PATH = "${env.WORKSPACE}"
        
        // Custom environment variables (modify as needed)
        NODE_ENV = 'production'
        // APP_VERSION = '1.0.0'
        // API_URL = 'https://api.example.com'
        
        // Java/Node/Python paths (uncomment if needed)
        // JAVA_HOME = '/usr/lib/jvm/java-11-openjdk'
        // PATH = "${env.PATH}:/usr/local/bin"
    }
    
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
                echo "Build Number: ${BUILD_NUMBER}"
                echo "Build Timestamp: ${BUILD_TIMESTAMP}"
                echo "Workspace: ${WORKSPACE_PATH}"
                checkout scm
            }
        }
        
        stage('Build') {
            steps {
                echo 'Building the project...'
                echo "Environment: ${NODE_ENV}"
                echo "Build ID: ${BUILD_ID}"
                
            }
        }
        
        stage('Test') {
            steps {
                echo 'Running tests...'
                echo "Testing with Build Number: ${BUILD_NUMBER}"
                
            }
        }
        
        stage('Archive') {
            steps {
                echo 'Archiving build artifacts...'
                echo "Archiving from: ${WORKSPACE_PATH}"
                
            }
        }
    }
    
    post {
        always {
            echo 'Pipeline completed. Cleaning up...'
            echo "Final Build Number: ${BUILD_NUMBER}"
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
