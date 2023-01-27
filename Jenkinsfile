pipeline {
    agent any

    stages {

        stage ('Build Docker image'){
            steps {
                script {
                    dockerapp = docker.build("juvinix/kube-news:${env.BUILD_ID}", '-f ./src/Dockerfile ./src')
                }
            }
        }
        stage ('Push Docker Image'){
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub')
                        dockerapp.push{'latest'}
                        dockerapp.push{"${env.BUILD_ID}"}
                }
            }
        }
    }
}