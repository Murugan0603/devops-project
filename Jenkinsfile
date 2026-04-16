pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "murugan0603/devops-app"
    }

    stages {

        stage('Clone') {
            steps {
                git branch: 'main', url: 'https://github.com/Murugan0603/devops-project.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                dir('app') {
                    bat 'docker build -t %DOCKER_IMAGE% .'
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                bat 'docker login -u murugan0603 -p dckr_pat_lDJTc_vYxFUeV_prl9vioHUEaQw'
                bat 'docker push %DOCKER_IMAGE%'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                bat 'kubectl apply -f k8s/'
            }
        }
    }
}
