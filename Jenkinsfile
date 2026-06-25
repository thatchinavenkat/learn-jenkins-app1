pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:18-alphine'
                    reUseNode true  
                } 
            }
            steps {
                sh '''
                    ls -la 
                    node --version 
                    npn --version 
                    npm ci 
                    npm run build
                '''
            }
        }
    }
}
 