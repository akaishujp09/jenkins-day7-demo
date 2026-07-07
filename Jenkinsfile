pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Code pulled from Git'
            }
        }

        stage('Maven Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Verify Package') {
            steps {
                sh '''
                echo "Checking target folder"
                ls -ltr target/
                '''
            }
        }
    }

    post {
        success {
            echo 'Maven build successful'
        }
        failure {
            echo 'Maven build failed'
        }
    }
}
