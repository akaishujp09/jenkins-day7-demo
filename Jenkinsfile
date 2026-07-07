pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Pulling code from Git'
            }
        }

        stage('Build') {
            steps {
                sh 'echo Building application'
            }
        }

        stage('Test') {
            steps {
                sh 'echo Running test cases'
            }
        }

        stage('Package') {
            steps {
                sh 'echo Creating package'
            }
        }

        stage('Deploy') {
            steps {
                sh 'echo Deploying application'
            }
        }
    }
}
