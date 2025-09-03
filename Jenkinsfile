        pipeline {
            agent any 
            tools {
                maven 'Maven3'   
                jdk 'Java11'     
            }
            triggers {
                githubPush()   
            }

            stages {
                stage('Checkout') {
                    steps {
                    echo "Cloning repository..."
                    git branch: 'jenkinsAssignment', url: 'https://git-training.nagarro.com/nagarro_fresher_training/automation-manual-qa/rahul-3218404.git'
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
    }