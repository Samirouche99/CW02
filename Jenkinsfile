pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    // Build Docker image
                    docker.build("samirouche99/nodejs-web-app")
                }
            }
        }
        stage('Push to DockerHub') {
            steps {
                script {
                    // Push Docker image to DockerHub
                    docker.withRegistry('https://registry.hub.docker.com', 'Dockerhub') {
                        docker.image("samirouche99/nodejs-web-app").push()
                    }
                }
            }
        }
    }
}
#Testing
