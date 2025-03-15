pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-rahul2', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://ADDB96A991BA83AA2FFE414112A2CA4A.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-rahul2', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://ADDB96A991BA83AA2FFE414112A2CA4A.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
