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
            }
            catch (err) {                                        
                unstable(message: "${STAGE_NAME} is unstable")
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

    // Define global post actions (optional)
    post {
        always {
            // Clean up any temporary files or resources
            deleteDir()
        }
    }
}
