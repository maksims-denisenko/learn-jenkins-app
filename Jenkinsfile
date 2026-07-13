pipeline {
    agent any

    stages {
        stage('NO DOCKER') {
            steps {
                sh '''
                echo 'no Docker'
                ls -la
                '''
            }
        }

        stage('WITH DOCKER') {
            agent {
                docker {
                    image 'node:18-alpine'
                }
            }
            steps {
                sh '''
                echo "WITH DOCKER"
                ls -la
                '''

            }
        }
    }
}