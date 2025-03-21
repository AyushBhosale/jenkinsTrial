pipeline {
    agent any
    tools {
        maven 'DefaultMaven'  // Use the exact name you configured in Jenkins
    }
    environment {
        GIT_CREDENTIALS_ID = '0c651ffc-10ed-4b2d-a05b-f45c2cd2b267'  // Your credentials ID
        GIT_REPO_URL = 'https://github.com/AyushBhosale/jenkinsTrial.git'  // Correct repo URL
        BRANCH_NAME = 'main'  // Set the branch to checkout
    }
    stages {
        stage('Checkout Code') {
            steps {
                script {
                    echo 'Checking out code from GitHub...'
                    git branch: "${BRANCH_NAME}", credentialsId: "${GIT_CREDENTIALS_ID}", url: "${GIT_REPO_URL}"
                }
            }
        }
        stage('Build Application') {
            steps {
                script {
                    echo 'Building the application using Maven...'
                    bat 'mvn clean install'
                }
            }
        }
        stage('Run Tests') {
            steps {
                script {
                    echo 'Running test cases...'
                    bat 'mvn test'
                }
            }
        }
        stage('Deploy Application') {
            steps {
                script {
                    echo 'Deploying application...'
                    // Make sure deploy-script.bat exists or update this command
                    bat 'deploy-script.bat'
                }
            }
        }
    }
    post {
        success {
            echo 'Pipeline executed successfully! 🎉'
        }
        failure {
            echo 'Pipeline failed. Check logs for errors. ❌'
        }
    }
}
