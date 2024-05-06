pipeline {
    agent any

    stages {
        stage('Deploy to Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://A3C871983A664457EE6F8C3973A20A4B.gr7.ap-south-1.eks.amazonaws.com']]) {
                  sh "kubectl apply deployment-service.yml"
                  sleep 5
            }
        }        
    }
    stages {
        stage('Verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://A3C871983A664457EE6F8C3973A20A4B.gr7.ap-south-1.eks.amazonaws.com']]) {
                   sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
