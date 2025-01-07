pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-8', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://04BB07E46A01BD5483F353C7B4E2D2C8.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-8', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://04BB07E46A01BD5483F353C7B4E2D2C8.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
