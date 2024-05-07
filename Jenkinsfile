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
                    // Simulate test failure with 30% probability
                    def random = Math.random()
                    echo "Random number: ${random}"
                    if (random < 0.3) {
                        error 'Test failed!'
                    } else {
                        echo 'Test passed!'
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
