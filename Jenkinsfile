pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the project...'
                // Add your build steps here
            }
            post {
                success {
                    emailext body: "Build stage succeeded: ${env.BUILD_URL}",
                             subject: "Build Succeeded: ${env.JOB_NAME} - Build #${env.BUILD_NUMBER}",
                             to: '202018656@o6u.edu.eg'
                }
                failure {
                    emailext body: "Build stage failed: ${env.BUILD_URL}",
                             subject: "Build Failed: ${env.JOB_NAME} - Build #${env.BUILD_NUMBER}",
                             to: '202018656@o6u.edu.eg'
                }
            }
        }

        stage('Sign Code') {
            steps {
                script {
                    try {
                        pwd()
                        sh "salama.sh"
                    } catch (err) {
                        currentBuild.result = 'UNSTABLE'
                        echo "Sign Code stage is unstable: ${err}"
                    }
                }
            }
            post {
                success {
                    emailext body: "Sign Code stage succeeded: ${env.BUILD_URL}",
                             subject: "Sign Code Succeeded: ${env.JOB_NAME} - Build #${env.BUILD_NUMBER}",
                             to: '202018656@o6u.edu.eg'
                }
                failure {
                    emailext body: "Sign Code stage failed: ${env.BUILD_URL}",
                             subject: "Sign Code Failed: ${env.JOB_NAME} - Build #${env.BUILD_NUMBER}",
                             to: '202018656@o6u.edu.eg'
                }
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying the project...'
                // Add your deployment steps here
            }
            post {
                success {
                    emailext body: "Deploy stage succeeded: ${env.BUILD_URL}",
                             subject: "Deploy Succeeded: ${env.JOB_NAME} - Build #${env.BUILD_NUMBER}",
                             to: '202018656@o6u.edu.eg'
                }
                failure {
                    emailext body: "Deploy stage failed: ${env.BUILD_URL}",
                             subject: "Deploy Failed: ${env.JOB_NAME} - Build #${env.BUILD_NUMBER}",
                             to: '202018656@o6u.edu.eg'
                }
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
