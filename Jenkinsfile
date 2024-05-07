pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the project...'
                // Add your build steps here
            }
        }

        stage('Test') {
            steps {
                script {
                    try {
                        // Run your tests here
                        // Introduce an intentional error for demonstration
                        sh 'exit 1'
                    } catch (Exception e) {
                        // Handle the test failure gracefully
                        echo 'Test failed but continuing...'
                    }
                }
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying the project...'
                // Add your deployment steps here
                // This stage will run even if the test stage fails
            }
        }
    }
