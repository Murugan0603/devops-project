pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "YOUR_DOCKER_USERNAME/devops-app"
    }

    stages {

        stage('Clone') {
            steps {
                git 'https://github.com/YOUR_USERNAME/YOUR_REPO.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $DOCKER_IMAGE ./app'
            }
        }

        stage('Push Docker Image') {
            steps {
                sh 'docker login -u YOUR_DOCKER_USERNAME -p YOUR_PASSWORD'
                sh 'docker push $DOCKER_IMAGE'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh 'kubectl apply -f k8s/'
            }
        }
    }
}