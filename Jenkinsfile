pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://EE3EE2C427C0F9999D221368AF9E16F5.gr7.ap-southeast-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://EE3EE2C427C0F9999D221368AF9E16F5.gr7.ap-southeast-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
