pipeline {
    agent any

    parameters {
        choice(
            name: 'choose pls',
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
            }
        }

        stage('Test') {
            when {
                expression { params.flag == 'true' }
            }
            steps {
                echo 'Running tests...'
            }
        }

        stage('Deploy') {
            when {
                expression { params.flag == 'true' }
            }
            steps {
                echo 'Deploying the project...'
            }
        }
    }

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

}
