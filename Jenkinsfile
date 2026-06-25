pipeline {
    agent any

    stages {
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
        stage('Test') {
            steps {
                sh '''
                    file="${WORKSPACE}/build/index.html"
                   
                    if [ -f "$file" ]; then
                        echo "File ${file} is present "
                    else 
                        echo "File ${file} is not present "
                    fi
                '''
            }

        }
    }
}
 