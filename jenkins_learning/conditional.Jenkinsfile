pipeline {
    agent any
    
    // Define boolean parameter
    parameters {
        booleanParam(name: 'RUN_TESTS', defaultValue: true, description: 'Run the test stage?')
    }
    
    stages {
        stage('Build') {
            steps {
                echo 'Building...'
            }
        }

        // Conditionally run the 'Test' stage based on the boolean parameter
        stage('Test') {
            when {
                expression {
                    return params.RUN_TESTS
                }
            }
            steps {
                echo 'Running tests...'
                // Add test-related steps here (e.g., executing unit tests)
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying...'
            }
        }
    }
}
