pipeline {
    agent any

    stages {
        stage('Deploy to kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-cred', namespace: 'webapps', serverUrl: 'https://D5CF2BFE9ED8EF41D0A38813470E5D54.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl -f apply deployment-service.yml"
                        sleep 60
                }
            }
        }
        stage('verify deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-cred', namespace: 'webapps', serverUrl: 'https://D5CF2BFE9ED8EF41D0A38813470E5D54.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
