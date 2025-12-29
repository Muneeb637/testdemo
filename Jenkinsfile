pipeline {
    agent any
    
    parameters {
        // String parameter
        string(name: 'APP_VERSION', defaultValue: '1.0.0', description: 'Application version to build')
        
        // Choice parameter (dropdown)
        choice(name: 'ENVIRONMENT', choices: ['development', 'staging', 'production'], description: 'Target environment')
        
        // Boolean parameter (checkbox)
        booleanParam(name: 'RUN_TESTS', defaultValue: true, description: 'Run tests during build')
        
        // Text parameter (multi-line)
        text(name: 'BUILD_NOTES', defaultValue: '', description: 'Build notes or comments')
        
        // Password parameter (hidden)
        // password(name: 'API_KEY', defaultValue: '', description: 'API Key for deployment')
    }
    
    environment {
        // Build information
        BUILD_NUMBER = "${env.BUILD_NUMBER}"
        BUILD_ID = "${env.BUILD_ID}"
        BUILD_TIMESTAMP = "${new Date().format('yyyy-MM-dd HH:mm:ss')}"
        
        // Workspace information
        WORKSPACE_PATH = "${env.WORKSPACE}"
        
        // Use parameters in environment
        NODE_ENV = "${params.ENVIRONMENT}"
        APP_VERSION = "${params.APP_VERSION}"
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
                echo "App Version: ${params.APP_VERSION}"
                echo "Environment: ${params.ENVIRONMENT}"
                checkout scm
            }
        }
        
        stage('Build') {
            steps {
                echo 'Building the project...'
                echo "Environment: ${NODE_ENV}"
                echo "Build ID: ${BUILD_ID}"
                echo "Building version: ${params.APP_VERSION}"
                
            }
        }
        
        stage('Test') {
            when {
                expression { params.RUN_TESTS == true }
            }
            steps {
                echo 'Running tests...'
                echo "Testing with Build Number: ${BUILD_NUMBER}"
                echo "Build Notes: ${params.BUILD_NOTES}"
                
            }
        }
        
        stage('Archive') {
            steps {
                echo 'Archiving build artifacts...'
                echo "Archiving from: ${WORKSPACE_PATH}"
                echo "Version: ${params.APP_VERSION}"
                
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
