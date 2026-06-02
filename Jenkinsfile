pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/ivishnureddy/helloDocker.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t hellodocker .'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh 'kubectl apply -f deploymentsvc.yaml'
            }
        }
    }
}
