pipeline {
    agent any

    stages {
        stage('Build & Tag Docker Image') {
            steps {
                script {
                    sh '''
                        echo 'your-password-or-token' | docker login -u bharathiraja3234 --password-stdin
                        docker build -t bharathiraja3234/adservice:latest .
                    '''
                }
            }
        }
        
        stage('Push Docker Image') {
            steps {
                script {
                    sh 'docker push bharathiraja3234/adservice:latest'
                }
            }
        }
    }
}
