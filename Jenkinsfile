pipeline {
    agent any
    
    tools {
        // Use exact names configured in Jenkins for Maven and JDK
        maven 'Maven'        // Change 'Maven' to your Maven installation name
        jdk 'java17'         // Change 'java11' to your JDK installation name
    }
    
    triggers {
        githubPush()
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
                bat 'mvn clean install'
            }
        }
        
        stage('Test') {
            steps {
                 bat 'mvn test'
            }
        }
        
        stage('Deploy') {
            steps {
                echo 'Deploying application...'
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
