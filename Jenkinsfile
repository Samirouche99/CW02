
#Testing
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from the repository
                checkout scm
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    // Build Docker image and tag it
                    docker.build("samirouche99/nodejs-web-app:latest -f Dockerfile .")
                }
            }
        }
        stage('Build Test') {
            steps {
                script {
                    // Run a command inside the container to ensure it has launched successfully
                    docker.image("samirouche99/nodejs-web-app:latest").inside {
                        sh 'echo "Container is running successfully!"'
                    }
                }
            }
        }
        stage('Push to DockerHub') {
            steps {
                script {
                    // Push Docker image to DockerHub
                    docker.withRegistry('https://registry.hub.docker.com', 'Dockerhub') {
                        docker.image("samirouche99/nodejs-web-app:latest").push()
                    }
                }
            }
        }
        stage('Deploy to Kubernetes') {
            steps {
                script {
                    // You may add Kubernetes deployment commands here
                    // For example, apply a Kubernetes manifest file
                    sh 'kubectl apply -f your-kubernetes-manifest.yaml'
                }
            }
        }
    }
}
