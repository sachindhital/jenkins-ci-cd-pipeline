pipeline {
    agent any
    environment {
        DIRECTORY_PATH = '/home/sachin/Desktop/Deakin'  // Replace with your code directory path
        TESTING_ENVIRONMENT = 'test-environment'
        PRODUCTION_ENVIRONMENT = 'Sachin'
    }
    stages {
        stage('Build') {
            steps {
                echo "fetch the source code from the directory path specified by the environment variable: ${env.DIRECTORY_PATH}"
                echo "compile the code and generate any necessary artifacts"
            }
        }
        stage('Test') {
            steps {
                echo 'unit tests'
                echo 'integration tests'
            }
        }
        stage('Code Quality Check') {
            steps {
                echo 'check the quality of the code'
            }
        }
        stage('Deploy') {
            steps {
                echo "deploy the application to a testing environment specified by the environment variable: ${env.TESTING_ENVIRONMENT}"
            }
        }
        stage('Approval') {
            steps {
                echo 'Waiting for approval...'
                sleep time:10, unit:'SECONDS'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo "deploy the code to the production environment: ${env.PRODUCTION_ENVIRONMENT}"
            }
        }
    }
}


