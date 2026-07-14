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
                test -f build/index.html
                npm test
                '''
            }
        }
        stage('E2E TEST') {
            agent {
                docker {
                    image 'mcr.microsoft.com/playwright:v1.61.0-noble'
                    reuseNode true
                }
            }
            steps {
                sh '''
                echo "E2E TEST STAGE"
                npm install serve
                node_modules/.bin/serve -s build -l 3000 &
                npx playwright test

                '''
            }
        }
    }
    post {
        always {
            junit 'test-results/junit.xml'
        }
    }
}