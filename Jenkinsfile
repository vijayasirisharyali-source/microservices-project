pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-siri', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://AED115AF19ADE40A5DA02257E0CFE9EC.gr7.ap-southeast-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-siri', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://AED115AF19ADE40A5DA02257E0CFE9EC.gr7.ap-southeast-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
