pipeline {
    agent any

    environment {
        AWS_CREDENTIALS_ID = 'aws-cred' 
    }
    stages {
        stage('git-checkout') {
        steps {
            git branch: 'main', url: 'https://github.com/chanduooo/deploy-nginx-.git'
        }
    }
        stage('Deploy to AWS') {
            steps {
                withAWS(credentials: "${AWS_CREDENTIALS_ID}") {
                    sh '''
                    # Example AWS CLI command
                    aws s3 ls
                    '''
                }
            }
        }
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
