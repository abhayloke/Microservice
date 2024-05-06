pipeline {
    agent any

    environment {
        KUBECONFIG = '/var/lib/jenkins/.kube/config'
    }

    stages {
        stage('Deploy to Kubernetes') {
            steps {
                script {
                    withKubeConfig([credentialsId: 'k8-token', serverUrl: 'https://A3C871983A664457EE6F8C3973A20A4B.gr7.ap-south-1.eks.amazonaws.com']) {
                        sh "kubectl apply -f deployment-service.yml -n webapps"
                        sleep 2
                    }
                }
            }
        }

        stage('Verify Deployment') {
            steps {
                script {
                    withKubeConfig([credentialsId: 'k8-token', serverUrl: 'https://A3C871983A664457EE6F8C3973A20A4B.gr7.ap-south-1.eks.amazonaws.com']) {
                        sh "kubectl get svc -n webapps"
                    }
                }
            }
        }
    }
}
