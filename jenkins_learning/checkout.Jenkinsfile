pipeline {
    agent any

    parameters {
        string(name: 'BRANCH_NAME', defaultValue: 'main', description: 'Git branch to build')
        choice(name: 'ENVIRONMENT', choices: ['dev', 'staging', 'prod'], description: 'Deployment environment')
    }

    environment {
        APP_NAME = 'my-app'
        VERSION = '1.0.0'
    }

    stages {
        stage('Checkout') {
            steps {
                echo "Checking out branch: ${params.BRANCH_NAME}"
                // git branch: "${params.BRANCH_NAME}", url: 'https://github.com/your-repo/your-project.git'
            }
        }

        stage('Build') {
            steps {
                sh """
                    echo 'Building ${env.APP_NAME} version ${env.VERSION}'
                """
            }
        }

        stage('Test') {
            steps {
                echo "Running tests for ${env.APP_NAME}"
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying ${env.APP_NAME} version ${env.VERSION} to ${params.ENVIRONMENT}"
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