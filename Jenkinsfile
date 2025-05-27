pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://7122F3D3B769477607CEA84A06034B36.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f kuberenetes-manfest-file.yaml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://7122F3D3B769477607CEA84A06034B36.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc"
                }
            }
        }
    }
}
