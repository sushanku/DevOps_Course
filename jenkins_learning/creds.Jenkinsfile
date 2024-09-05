pipeline {
    agent any

    parameters {
        string(name: 'BRANCH_NAME', defaultValue: 'main', description: 'Git branch to build')
        choice(name: 'ENVIRONMENT', choices: ['dev', 'staging', 'prod'], description: 'Deployment environment')
    }

    environment {
        APP_NAME = 'my-app'
        VERSION = '1.0.0'
        // Define credential IDs
        SERVER_CREDS = 'frontend_build_server'
        DEPLOY_CREDS = 'frontend_build_server'
    }

    stages {
        stage('Checkout') {
            steps {
                echo "Checking out branch: ${params.BRANCH_NAME}"
                withCredentials([usernamePassword(credentialsId: "${env.SERVER_CREDS}", usernameVariable: 'SERVER_USERNAME', passwordVariable: 'SERVER_PASSWORD')]) {
                    // Use credentials to checkout private repository
                    // git branch: "${params.BRANCH_NAME}", url: "https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/your-repo/your-project.git"
                    echo "Checked out with credentials for ${SERVER_USERNAME}"
                }
            }
        }

        stage('Build') {
            steps {
                sh """
                    echo 'Building ${env.APP_NAME} version ${env.VERSION}'
                """
                // Add your build commands here
            }
        }

        stage('Test') {
            steps {
                echo "Running tests for ${env.APP_NAME}"
                // Add your test commands here
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying ${env.APP_NAME} version ${env.VERSION} to ${params.ENVIRONMENT}"
                withCredentials([string(credentialsId: "${env.DEPLOY_CREDS}", variable: 'DEPLOY_KEY')]) {
                    // Use deploy key in your deployment script
                    sh """
                        echo "Deploying with key ${DEPLOY_KEY.take(4)}****"
                        # Your deployment script here
                        # Example: ./deploy.sh ${params.ENVIRONMENT} ${DEPLOY_KEY}
                    """
                }
            }
        }
    }

    post {
        success {
            echo "Pipeline for ${env.APP_NAME} completed successfully!"
        }
        failure {
            echo "Pipeline for ${env.APP_NAME} failed."
        }
    }
}