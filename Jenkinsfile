pipeline {
    agent any

    tools {
        maven 'Test_Maven'
    }

    environment {
        DEPLOY_DIR = "C:\\Users\\Rana\\apache-tomcat-11.0.9\\webapps" // adjust as per your Tomcat path
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Rohith1388/boxfuse-sample-java-war-hello'
            }
        }

        stage('Build') {
            steps {
                bat 'mvn clean package'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                bat 'copy target\\*.war %DEPLOY_DIR%\\hello.war'
            }
        }
    }

    post {
        success {
            echo '✅ Application successfully deployed to Tomcat!'
        }
        failure {
            echo '❌ Build or deployment failed.'
        }
    }
}
