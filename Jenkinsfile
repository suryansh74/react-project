pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
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
                    npm run build
                    ls -la                
                '''
            }
        }
        stage('Test')
        {
            steps{
                sh '''
                echo "Checking if there is index.html present in dist folder"
                find dist/index.html
                '''
            }
        }
    }
}
