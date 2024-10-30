pipeline {
    agent any

    environment {
        DEPLOY_ENV = 'staging'
        PROD_ENV = 'production'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building the application...'
                // Add build commands here
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                // Add test commands here
            }
        }

        stage('Package') {
            steps {
                echo 'Packaging the application...'
                // Add packaging commands here, e.g., Docker image creation
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging environment...'
                // Add staging deployment commands here
            }
        }

        stage('Approval') {
            steps {
                input message: 'Approve deployment to production?', ok: 'Approve'
            }
        }

        stage('Deploy to Production') {
            when {
                expression {
                    env.BRANCH_NAME == 'main' // restricts production deployment to the main branch
                }
            }
            steps {
                echo 'Deploying to production environment...'
                // Add production deployment commands here
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully.'
        }
        failure {
            echo 'Pipeline failed.'
            // Add notification commands here, e.g., Slack or email notifications
        }
    }
}
