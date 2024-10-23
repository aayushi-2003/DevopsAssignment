pipeline {
    agent any
    stages {
        stage('Verify Docker'){
            steps{
                script{
                    sh 'docker --version'
                }
            }
        }
        
        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t factorial-web-app .'
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    sh 'docker stop factorial-web-app || true'
                    sh 'docker rm factorial-web-app || true'

                    sh 'docker run -d -p 8090:80 factorial-web-app factorial-web-app'
                }
            }
        }
    }

    post {
        always {
            sh 'docker stop factorial-web-app || true'
            sh 'docker rm factorial-web-app || true'
        }
    }
}
