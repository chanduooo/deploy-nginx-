pipeline {
    agent any


    stages {
        
        stage('eks-connection') {
            steps {
                sh 'kubectl config use-context arn:aws:eks:us-east-2:191962495115:cluster/dev-eks'
            }
        }
        stage('deplo-nginx') {
            steps {
                sh '''
                   kubectl apply -f deployment-nginx.yaml
                   kubectl apply -f service-nginx.yaml
                   ''' 
            }
        }
        stage('checking pod status') {
            steps {
                sh 'kubectl get pods'
            }
        }
    }
}
