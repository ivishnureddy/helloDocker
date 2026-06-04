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
                sh 'docker build --network host -t hellodocker .'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh '''
                echo $KUBECONFIG
                pwd
                ls -la

                sleep 10
                
                kubectl get nodes
                kubectl apply -f $WORKSPACE/deploymentsvc.yaml
                '''
            }
        }
    }
}
