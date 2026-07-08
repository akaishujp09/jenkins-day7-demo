pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t my-web-app:v1 .'
            }
        }

        stage('Remove Old Container') {
            steps {
                sh 'docker rm -f my-web-container || true'
            }
        }

        stage('Run New Container') {
            steps {
                sh 'docker run -d --name my-web-container -p 8081:80 my-web-app:v1'
            }
        }

        stage('Verify') {
            steps {
                sh '''
                docker ps
                curl -I http://localhost:8081 || true
                '''
            }
        }
    }

    post {
        success {
            echo 'Docker container deployed successfully'
        }
        failure {
            echo 'Docker container deployment failed'
        }
    }
}
