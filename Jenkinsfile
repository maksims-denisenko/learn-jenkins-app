pipeline {
    agent any

    stages {
        stage('WITH DOCKER') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                echo "WITH DOCKER"
                ls -la
                node --version
                npm --version
                npm ci
                npm run build
                ls -la
                '''

            }
        }
    }
}