pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    // Build the Docker image
                    sh 'docker build -t factorial-web-app .'
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    // Stop any existing container with the same name
                    sh 'docker stop factorial-web-app || true'
                    sh 'docker rm factorial-web-app || true'

                    // Run the Docker container
                    sh 'docker run -d -p 8080:80 --name factorial-web-app factorial-web-app'
                }
            }
        }
    }

    post {
        always {
            // Cleanup
            sh 'docker stop factorial-web-app || true'
            sh 'docker rm factorial-web-app || true'
        }
    }
}
