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
                    echo 'Creating file archive...'
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

    // Define global post actions
    post {
        always {
            script {
                def jobName = env.JOB_NAME
                def buildStatus = currentBuild.currentResult
                echo "Sending email notification for ${jobName} - ${buildStatus}"
                emailext subject: "Job Status: ${jobName} - ${buildStatus}",
                          body: "The job ${jobName} has finished with status: ${buildStatus}.\n\n${BUILD_URL}",
                          to: '202018656@o6u.edu.eg'
            }
        }
    }
}
