pipeline {
    agent any
   tools {
        git 'default-git' // Replace 'default-git' with the name you configured
        nodejs 'my-nodejs'
    }
    stages {
        stage('Install Dependencies') {
            steps {
                script {
                    try {
                        echo 'Installing dependencies...'
                        cleanWs() // Clean workspace before starting
                        sh 'npm install --verbose'
                    } catch (Exception e) {
                        echo "Error during dependency installation: ${e}"
                        error "Stage 'Install Dependencies' failed."
                    }
                }
            }
        }
        stage('Build') {
            steps {
                script {
                    try {
                        echo 'Building the Next.js application...'
                        sh 'npm run build'
                    } catch (Exception e) {
                        echo "Error during build: ${e}"
                        error "Stage 'Build' failed."
                    }
                }
            }
        }
        stage('Start') {
            steps {
                script {
                    try {
                        echo 'Starting the Next.js application...'
                        sh 'npm run start'
                        echo 'Next.js application started successfully.'
                    } catch (Exception e) {
                        echo "Error during application start: ${e}"
                        error "Stage 'Start' failed."
                    }
                }
            }
        }
    }
    post {
        always {
            echo 'Pipeline execution completed.'
        }
        success {
            echo 'Pipeline executed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check the logs for details.'
        }
    }
}
