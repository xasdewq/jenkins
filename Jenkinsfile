pipeline {
    agent any
    
    tools {
        // Use exact names configured in Jenkins for Maven and JDK
        maven 'Maven'        // Change 'Maven' to your Maven installation name
        jdk 'java17'         // Change 'java11' to your JDK installation name
    }
    
    triggers {
        // For demo, polling every 5 minutes. Replace with webhook as needed.
        pollSCM('H/5 * * * *')
    }
    
    stages {
        stage('Checkout') {
            steps {
                echo "Cloning repository..."
                git branch:'main', url: 'https://github.com/xasdewq/jenkins.git'
            }
        }
        
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
        
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        
        stage('Deploy') {
            steps {
                echo 'Deploying application...'
                // Add your deployment scripts/commands here
            }
        }
        
        stage('Cleanup') {
            steps {
                echo 'Cleaning up workspace...'
                cleanWs()
            }
        }
    }
    
    post {
        always {
            echo 'Pipeline finished.'
        }
        success {
            echo 'Pipeline succeeded!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
