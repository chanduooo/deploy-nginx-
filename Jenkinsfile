pipeline {
    agent any
    environment {
        AWS_ACCESS_KEY_ID = credentials('aws-cred')  
        AWS_DEFAULT_REGION = 'us-east-2'
    }
    stages {
        stage('git-checkout') {
        steps {
            git branch: 'main', url: 'https://github.com/chanduooo/deploy-nginx-.git'
        }
    }
        stage('Deploy to AWS') {
            steps {
                        sh 'aws s3 ls'
            }
    }
        stage('connection eks') {
            steps {
                        sh 'aws eks --region us-east-2 update-kubeconfig --name dev-eks'
            }
}
        stage('nodes status') {
            steps {
                        sh 'kubectl get nodes'
            }
}
        stage('deploy-nginx') {
            steps {
                        sh '''
                            kubectl apply -f deployment-nginx.yaml
                            kubectl apply -f service-nginx.yaml
                            '''
            }
}
}
}
