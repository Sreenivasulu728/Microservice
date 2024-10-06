pipeline {
    agent any

    stages {
        stage('Deploy to kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-cred', namespace: 'webapps', serverUrl: 'https://18D4B4D1021424C0DD588687281362B5.yl4.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl -f apply deployment-service.yml"
                        sleep 60
                }
                
            }
        }
        stage('verify deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-cred', namespace: 'webapps', serverUrl: 'https://18D4B4D1021424C0DD588687281362B5.yl4.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
