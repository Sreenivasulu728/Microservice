pipeline {
    agent any

    stages {
        stage('Build & Tag Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-cred') {
                        sh "docker build -t sreenu728/checkoutservice:latest ."
                    }
                }
            }
        }
        
        stage('Push Docker Image') {
            steps {
                script {
                     withDockerRegistry(credentialsId: 'docker-cred') {
                        sh "docker push sreenu728/checkoutservice:latest"
                    }
                }
            }
        }
    }
}
