pipeline {
    agent any

    stages {
        stage('Deployment to Kubernetes') {
            steps {
                withKubeCredentials(
                    kubectlCredentials: [[
                        caCertificate: '', 
                        clusterName: 'EKS-1', 
                        contextName: '', 
                        credentialsId: 'k8-token', 
                        namespace: 'webapps', 
                        serverUrl: 'https://68087C52B99A899BD073DE439055C58B.sk1.eu-north-1.eks.amazonaws.com'
                    ]]
                ) {
                    sh 'kubectl apply -f deployment-service.yml'
                }
            }
        }
        
        stage('Verify the Deployment') {
            steps {
                withKubeCredentials(
                    kubectlCredentials: [[
                        caCertificate: '', 
                        clusterName: 'EKS-1', 
                        contextName: '', 
                        credentialsId: 'k8-token', 
                        namespace: 'webapps', 
                        serverUrl: 'https://68087C52B99A899BD073DE439055C58B.sk1.eu-north-1.eks.amazonaws.com'
                    ]]
                ) {
                    sh 'kubectl get svc -n webapps'
                    sh 'kubectl get pods -n webapps'
                }
            }
        }
    }
}
