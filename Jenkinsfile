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
                    } catch (err) {
                        // Log the error message
                        echo "Test failed with error: ${err.message}"
                    } finally {
                        // This block will always run, regardless of whether there was an error
                        echo 'Test stage complete.'
                    }
                }
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying the project...'
                // Add your deployment steps here
            }
        }
    }

    // Define global post actions (optional)
    post {
        always {
            // Clean up any temporary files or resources
            deleteDir()
        }
    }
}
