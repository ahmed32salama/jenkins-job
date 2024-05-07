pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the project...'
                sh 'touch file1'
            }
            post {
                success {
                    echo 'Creating file archive'
                    archiveArtifacts artifacts: 'file1', allowEmptyArchive: true
                }
                failure {
                    echo 'Build failed, skipping file archive creation.'
                }
            }
        }

         stage('Run Smoke and Integration Tests') {
            parallel {
                stage('Smoke Test') {
                    steps {
                        echo 'Running smoke tests...'
                        // Add your smoke test steps here
                    }
                }
                stage('Integration Test') {
                    steps {
                        echo 'Running integration tests...'
                    }
                }
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying the project...'
            }
        }
    }

   post {
        always {
            deleteDir()
        }
        success {
            emailext body: 'Build successful',
                      subject: 'Build successful',
                      to: 'seaea.32@gmail.com',
                      attachmentsPattern: 'file1'
        }
        failure {
            emailext body: 'Build failed',
                      subject: 'Build failed',
                      to: 'seaea.32@gmail.com',
                      attachmentsPattern: 'file1'
        }
    }
}
