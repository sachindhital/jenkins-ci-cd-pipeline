pipeline {
    agent any

    environment {
        // Define environment variables here
        GITHUB_REPO_URL = 'https://github.com/sachindhital/jenkins-ci-cd-pipeline.git'
        STAGING_SERVER = 'staging.example.com'
        PRODUCTION_SERVER = 'production.example.com'
        EMAIL_RECIPIENT = 'sachin.work75@gmail.com'
        MAVEN_HOME = tool 'Maven 3.6.3' // Example of using a Jenkins tool
    }

    stages {
        stage('Build') {
            steps {
                echo "Building the code from ${GITHUB_REPO_URL}"
                // Example: sh "${MAVEN_HOME}/bin/mvn clean package"
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit tests with JUnit and integration tests to ensure the components work together.'
                // Example: sh "${MAVEN_HOME}/bin/mvn test"
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Performing code analysis using SonarQube or a similar tool.'
                // Example: sh 'sonar-scanner'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Performing a security scan using OWASP Dependency-Check or a similar tool.'
                // Example: sh 'dependency-check.sh --scan .'
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo "Deploying the application to the staging server at ${STAGING_SERVER}."
                // Example: sh "ssh deploy@${STAGING_SERVER} 'deploy-script.sh'"
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on the staging environment.'
                // Example tool: Post-deployment integration testing
                // sh './run-integration-tests.sh'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo "Deploying the application to the production server at ${PRODUCTION_SERVER}."
                // Example: sh "ssh deploy@${PRODUCTION_SERVER} 'deploy-script.sh'"
            }
        }
    }

    post {
        always {
            echo 'Pipeline completed.'
        }

        success {
            mail to: "${EMAIL_RECIPIENT}",
                 subject: "SUCCESS: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
                 body: "Good news! The pipeline completed successfully. Check Jenkins for details."
        }

        failure {
            mail to: "${EMAIL_RECIPIENT}",
                 subject: "FAILURE: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
                 body: "Unfortunately, the pipeline failed. Please check the logs in Jenkins for more details."
        }
    }
}
