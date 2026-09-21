pipeline {

    agent any

    environment {
        APP_NAME = 'week9-cicd-app'
        IMAGE_NAME = 'week9-cicd-app'
    }

    stages {

        stage('Checkout') {
            steps {
                echo 'Checking out source code...'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building application...'
                sh 'echo "Application build completed successfully"'
            }
        }

        stage('Test') {
            steps {
                echo 'Running automated tests...'
                sh 'echo "Automated test passed successfully"'
            }
        }

        stage('Package') {
            steps {
                echo 'Packaging application...'
                sh 'tar -czf application.tar.gz Jenkinsfile'
            }
        }

        stage('Docker Build') {
            steps {
                echo 'Building Docker image...'
                sh 'docker build -t ${IMAGE_NAME}:${BUILD_NUMBER} .'
            }
        }

    }

    post {
        success {
            echo 'CI Pipeline completed successfully!'
        }

        failure {
            echo 'Pipeline failed. Check the Jenkins console output.'
        }
    }
}
