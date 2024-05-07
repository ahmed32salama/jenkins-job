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
                
            }
        }
    }

    // Define global post actions
    post {
        always {
            script {
                #def buildStatus = currentBuild.currentResult.toString()
                #def buildUrl = env.BUILD_URL
                #def buildNumber = env.BUILD_NUMBER
                def jobName = env.JOB_NAME
                #def subject = "Pipeline Status: ${jobName} - Build #${buildNumber} - ${buildStatus}"
                #def body = """
                #Build Status: ${buildStatus}
                #Build Number: ${buildNumber}
                Job Name: ${jobName}
                #Build URL: ${buildUrl}

                Stage Status:
                Build: ${currentBuild.getBuildStatusSummary('Build')}
                Sign Code: ${currentBuild.getBuildStatusSummary('Sign Code')}
                Deploy: ${currentBuild.getBuildStatusSummary('Deploy')}
                """

                emailext body: body, subject: subject, to: '202018656@o6u.edu.eg'
            }
        }
    }
}
