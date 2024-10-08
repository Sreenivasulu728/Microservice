pipeline {
    agent any

    stages {
        stage('Build & Tag Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-cred') {
                        sh "docker build -t sreeenu/adservice:latest ."
                    }
                }
            }
        }
        
        stage('Push Docker Image') {
            steps {
                script {
                     withDockerRegistry(credentialsId: 'docker-cred') {
                        sh "docker push sreeenu/adservice:latest"
                    }
                }
            }
        }
    }
}
