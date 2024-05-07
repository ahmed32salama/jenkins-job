pipeline {
    agent any

    parameters {
        choice(
            name: 'flag',
            choices: ['true', 'false'],
            description: 'Flag to determine pipeline execution'
        )
    }

    stages {
        stage('Build') {
            when {
                expression { params.flag == 'true' }
            }
            steps {
                echo 'Building the project...'
                // Add your build steps here
            }
        }

        stage('Test') {
            when {
                expression { params.flag == 'true' }
            }
            steps {
                echo 'Running tests...'
                // Add your test steps here
            }
        }

        stage('Deploy') {
            when {
                expression { params.flag == 'true' }
            }
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
        success {
            echo 'Pipeline executed successfully.'
        }
        failure {
            echo 'Pipeline was not executed.'
        }
    }

    options {
        skipDefaultCheckout() // Skip the default checkout to avoid checking out the code if the pipeline is not executed
    }
}
