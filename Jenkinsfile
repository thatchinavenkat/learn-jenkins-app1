pipeline {
    agent any

    stages {
        stage('Fileexist or not') {
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
