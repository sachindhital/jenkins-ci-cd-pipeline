pipeline {
    agent any

    environment {
        DIRECTORY_PATH = '/home/sachin/Desktop/Deakin'  // Replace with your code directory path
        TESTING_ENVIRONMENT = 'test-environment'
        PRODUCTION_ENVIRONMENT = 'Sachin'
        EMAIL_RECIPIENT = 'sachin.work75@gmail.com' // Your email address for notifications
    }
    
    stages {
        stage('Build') {
            steps {
                echo 'Building the code using Maven or a similar tool.'
                echo "fetch the source code from the directory path specified by the environment variable: ${env.DIRECTORY_PATH}"
                echo "compile the code and generate any necessary artifacts"
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit tests with JUnit and integration tests to ensure the components work together.'
                echo 'unit tests'
                echo 'integration tests'
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Performing code analysis using SonarQube or a similar tool.'
                echo 'check the quality of the code'
            }
        }

        stage('Deploy to Testing Environment') {
            steps {
                echo "deploy the application to a testing environment specified by the environment variable: ${env.TESTING_ENVIRONMENT}"
            }
        }

        stage('Security Scan and Approval') {
            steps {
                echo 'Performing a security scan using OWASP Dependency-Check or a similar tool.'
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

    post {
        always {
            echo 'Pipeline completed.'
        }
        success {
            //mail to: "${env.EMAIL_RECIPIENT}",
               //  subject: "SUCCESS: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
               //  body: "Good news! The pipeline completed successfully. Check Jenkins for details."
        }
        failure {
           // mail to: "${env.EMAIL_RECIPIENT}",
             //    subject: "FAILURE: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
             //    body: "Unfortunately, the pipeline failed. Please check the logs in Jenkins for more details."
        }
    }
}
