pipeline {
    agent any

    stages {
        stage('Deploy to Kubernetes') {
            steps {
                script {
                    withKubeCredentials(
                        credentialsId: 'k8-token',
                        caCertificate: '',
                        serverUrl: 'https://A3C871983A664457EE6F8C3973A20A4B.gr7.ap-south-1.eks.amazonaws.com',
                        clusterName: 'EKS-1',
                        namespace: 'webapps'
                    ) {
                        sh "kubectl apply -f deployment-service.yml"
                        sleep 5
                    }
                }
            }
        }

        stage('Verify Deployment') {
            steps {
                script {
                    withKubeCredentials(
                        credentialsId: 'k8-token',
                        caCertificate: '',
                        serverUrl: 'https://A3C871983A664457EE6F8C3973A20A4B.gr7.ap-south-1.eks.amazonaws.com',
                        clusterName: 'EKS-1',
                        namespace: 'webapps'
                    ) {
                        sh "kubectl get svc -n webapps"
                    }
                }
            }
        }
    }
}
