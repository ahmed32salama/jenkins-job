pipeline {
    agent any

    parameters {
        choice(
            name: 'flag',
            choices: ['true', 'false'],
            description: 'Flag to determine pipeline behavior'
        )
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building the project...'
            }
            post {
                success {
                    echo 'Creating file archive...'
                    archiveArtifacts artifacts: 'file1', allowEmptyArchive: true
                }
                failure {
                    echo 'Build failed, skipping file archive creation.'
                }
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying the project'

            }
        }
    }

    // Define global post actions (optional)
    post {
        always {
            deleteDir()
        }
        success {
            script {
                if (params.flag == 'true') {
                    echo 'Flag is true continuing with the pipeline.'
                } else if (params.flag == 'false') {
                    echo 'scape for the pipeline'
                } else {
                    error "Invalid flag value: ${params.flag}"
                }
            }
        }
    }
}
