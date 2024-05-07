pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the project...'
                // Add your build steps here
            }
        }

         stage('teast') {
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
        }
        stage('Deploy') {
            steps {
                echo 'Deploying the project...'
                // Add your deployment steps here
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
