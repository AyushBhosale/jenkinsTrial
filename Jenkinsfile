pipeline {
    agent any

    tools {
        maven "MAVEN"
        jdk "JDK"
    }

    stages {
        stage('Initialize') {
            steps {
                script {
                    env.M2_HOME = "/opt/maven"  // Set Maven home if needed
                }
                echo "PATH = ${env.M2_HOME}/bin:${env.PATH}"
                echo "M2_HOME = ${env.M2_HOME}"
            }
        }

        stage('Build') {
            steps {
                dir("/var/lib/jenkins/workspace/demopipelinetask/my-app") {
                    sh 'mvn -B -DskipTests clean package'
                }
            }
        }

        stage('Test') {
            steps {
                dir("/var/lib/jenkins/workspace/demopipelinetask/my-app") {
                    sh 'mvn test'
                }
            }
        }
    }

    post {
        always {
            junit allowEmptyResults: true, testResults: 'my-app/target/surefire-reports/*.xml'
        }
    }
}
