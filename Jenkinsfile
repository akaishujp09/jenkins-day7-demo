pipeline {
    agent any

    environment {
        JAVA_HOME = '/usr/lib/jvm/java-21-amazon-corretto.x86_64'
        PATH = "${JAVA_HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Check Java and Maven') {
            steps {
                sh '''
                java -version
                mvn -version
                '''
            }
        }

        stage('Maven Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Verify Package') {
            steps {
                sh 'ls -ltr target/'
            }
        }
    }

    post {
        success {
            archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            echo 'Maven build successful'
        }
        failure {
            echo 'Maven build failed'
        }
    }
}
