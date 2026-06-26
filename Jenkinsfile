pipeline {
    agent any

    stages {
        /*
        stage('Build') {
            agent {
                docker {
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
                    npm run build
                    ls -la
                '''
            }
        }
        */
        stage('Test') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true  
                } 
            }
            steps {
                sh '''
                    file="${WORKSPACE}/build/index.html"
                   
                    if [ -f "$file" ]; then
                        echo "File ${file} is present "
                    else 
                        echo "File ${file} is not present "
                    fi
                    npm test
                '''
            }
        }

         stage('E2E') {
            agent {
                docker {
                    image 'mcr.microsoft.com/playwright:v1.61.0-noble'
                    reuseNode true  
                } 
            }
            steps {
                sh '''
                    npm install serve
                    learn-jenkins-app1/node_modules/.bin/serve -s build
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
 