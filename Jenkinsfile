pipeline {
    agent any
    
    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/Lokesh-Soft-Dev/jenkins-ci-cd-demo.git'
                echo '✅ Successfully downloaded code from GitHub'
            }
        }
        
        stage('Build Status') {
            steps {
                echo '✅ Build completed successfully'
                echo '📝 This demonstrates a basic Jenkins pipeline'
                echo '🔧 Docker deployment would be configured in production'
            }
        }
    }
    
    post {
        always {
            echo '🚀 Jenkins pipeline execution completed'
        }
    }
}