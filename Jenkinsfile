pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the project...'
                // Add your build steps here
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
                failure {
                    emailext body: "Sign Code stage failed: ${env.BUILD_URL}",
                             subject: "Pipeline Failed: ${env.JOB_NAME} - Build #${env.BUILD_NUMBER}",
                             to: 'seaea.32@gmail.com'
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
