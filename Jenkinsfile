pipeline {
    agent any

    stages {
        stage('Build') {
            agent{
                docker{
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    ls -la
                    node --version
                    npm --version
                    npm ci
                    npm install --save-dev jest-junit
                    npm run build
                    ls -la
                '''
            }
        }

        stage('Test'){
            agent{
                docker{
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps{
                sh''' 
                    test -f build/index.html
                    npm test
                '''
            }
        }

        stages {
        stage('Deploy') {
            agent{
                docker{
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''

                '''
            }
        }
    }
    post{
            always{
                junit 'test-results/junit.xml'
            }
        }
    }
}