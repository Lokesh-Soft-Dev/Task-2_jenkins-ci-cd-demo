pipeline {
    agent any
    
    tools {
        nodejs 'nodejs'  // This will be configured in Jenkins later
    }
    
    stages {
        // Stage 1: Checkout code from GitHub
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Lokesh-Soft-Dev/jenkins-ci-cd-demo.git'
                echo '✅ Code checkout completed'
            }
        }
        
        // Stage 2: Install dependencies and test
        stage('Build & Test') {
            steps {
                sh 'npm install'
                sh 'npm test'
                echo '✅ Build and test completed'
            }
        }
        
        // Stage 3: Build Docker image
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t lokeshdocker143/nodejs-jenkins-demo:latest .'
                echo '✅ Docker image built successfully'
            }
        }
        
        // Stage 4: Deploy application
        stage('Deploy') {
            steps {
                sh '''
                # Stop and remove existing container if running
                docker stop nodejs-jenkins-app || true
                docker rm nodejs-jenkins-app || true
                
                # Run new container
                docker run -d -p 3002:3000 --name nodejs-jenkins-app lokeshdocker143/nodejs-jenkins-demo:latest
                '''
                echo '✅ Application deployed successfully'
            }
        }
    }
    
    post {
        always {
            echo 'Pipeline completed - check logs for details'
        }
        success {
            echo '🎉 Pipeline succeeded! App is running on http://localhost:3002'
            sh 'docker ps | grep nodejs-jenkins-app'
        }
        failure {
            echo '❌ Pipeline failed! Check the logs above for errors.'
        }
    }
}