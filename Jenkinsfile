pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
              withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'KaspaCluster', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://8249E47DE019B47FA051885FB135670A.gr7.ap-south-1.eks.amazonaws.com']])
                    sh "kubectl apply -f deployment-service.yml"
                      sleep 60
                
                }
            }
        }
        
        stage('Verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://9F39F577334FF23706994135261985F2.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
