pipeline {
    agent any

    stages {
        stage('BUILD') {
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
        stage('TEST') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                echo "TEST STAGE"
                ls -la |grep index.html


                '''
            }
        }
    }
}