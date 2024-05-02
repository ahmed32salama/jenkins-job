pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'echo "Building..."'
            }
        }
        stage('Test') {
            steps {
                // Replace this with your test commands
                sh 'echo "Testing..."'
            }
        }
        stage('Deploy') {
            steps {
                // Replace this with your deploy commands
                sh 'echo "Deploying..."'
            }
        }
    }

    post {
        success {
            // Notify success (optional)
            echo 'Pipeline succeeded!'
        }
        failure {
            // Notify failure (optional)
            echo 'Pipeline failed!'
        }
    }
}
