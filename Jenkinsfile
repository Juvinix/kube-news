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
                        docker.push('latest')
                        docker.push("${env.BUILD_ID}")
                }
            }
        }
    }
<<<<<<< HEAD
}
=======
}
>>>>>>> ceec047383f5c4b5aff88b1c1c2bb14fcb2d4919
