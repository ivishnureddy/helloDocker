pipeline {
    agent any

    environment{
        KUBECONFIG = "/var/jenkins_home/kubeconfig"
    }
    stages {
        stage('Clone') {
            steps {
                echo 'Repository already checked out by jenkins SCM' 
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t hellodocker .'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh '''
                echo $KUBECONFIG
                kubectl get nodes
                kubectl apply -f deploymentsvc.yaml
                '''
            }
        }
    }
}
