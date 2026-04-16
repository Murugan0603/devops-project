pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "Murugan0603/devops-app"
    }

    stages {

        stage('Clone') {
    steps {
        git branch: 'main', url: 'https://github.com/Murugan0603/devops-project.git'
    }
}

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $DOCKER_IMAGE ./app'
            }
        }

        stage('Push Docker Image') {
            steps {
                sh 'docker login -u Murugan0603 -p YOUR_PASSWORD'
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
