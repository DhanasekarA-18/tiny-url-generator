pipeline {
    agent any
    tools { nodejs 'my-nodejs' } // Ensure 'my-nodejs' is configured in Jenkins
    stages {
        stage('Install Dependencies') {
            steps {
                script {
                    sh 'npm install'
                }
            }
        }
        stage('Build') {
            steps {
                script {
                    sh 'npm run build'
                }
            }
        }
        stage('Start') {
            steps {
                script {
                    sh 'npm run start'
                }
                echo 'Next.js application started successfully.'
            }
        }
    }
}
