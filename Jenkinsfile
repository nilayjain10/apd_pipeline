pipeline {
    agent any

    stages {
        stage('Pull from Git') {
            steps {
                echo 'Cleaning workspace and pulling latest code...'
                // Jenkins usually handles the checkout if configured in the job, 
                // but this step ensures it's explicitly tracked.
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Executing Build Script...'
                bat 'Build.bat'
            }
        }

        stage('Test') {
            steps {
                echo 'Executing Test Script...'
                bat 'Test.bat'
            }
        }

        stage('Quality Check') {
            steps {
                echo 'Executing Quality Analysis...'
                bat 'Quality.bat'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Executing Deployment Script...'
                bat 'Deploy.bat'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Please check the batch script logs.'
        }
    }
}
