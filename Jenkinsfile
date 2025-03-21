pipeline {
    agent any
    tools {
        maven 'MAVEN'
    }
    environment {
        GIT_CREDENTIALS_ID = '0c651ffc-10ed-4b2d-a05b-f45c2cd2b267'
        GIT_REPO_URL = 'https://github.com/AyushBhosale/jenkinsTrial.git'
        BRANCH_NAME = 'main'
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
                    // Check if pom.xml exists before trying to build
                    if (fileExists('pom.xml')) {
                        bat 'mvn clean install'
                    } else {
                        echo 'No pom.xml found. Creating a simulated build for demo purposes.'
                        bat 'echo "Build simulation successful" > build.log'
                        bat 'type build.log'
                    }
                }
            }
        }
        stage('Run Tests') {
            steps {
                script {
                    echo 'Running test cases...'
                    if (fileExists('pom.xml')) {
                        bat 'mvn test'
                    } else {
                        echo 'No pom.xml found. Creating a simulated test for demo purposes.'
                        bat 'echo "Test simulation successful" > test.log'
                        bat 'type test.log'
                    }
                }
            }
        }
        stage('Deploy Application') {
            steps {
                script {
                    echo 'Deploying application...'
                    // Simulate deployment instead of using deploy-script.bat
                    bat 'echo "Deployment simulation completed successfully" > deploy.log'
                    bat 'type deploy.log'
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
