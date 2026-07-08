pipeline {
    agent any

    stages {
        stage('Check Docker') {
            steps {
                sh '''
                echo "Checking Docker version"
                docker version
                '''
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t my-web-app:v1 .'
            }
        }

        stage('Check Image') {
            steps {
                sh 'docker images | grep my-web-app'
            }
        }
    }

    post {
        success {
            echo 'Docker image build successful'
        }
        failure {
            echo 'Docker image build failed'
        }
    }
}
