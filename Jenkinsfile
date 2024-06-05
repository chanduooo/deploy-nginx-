pipeline {
    agent any
    stages {
        stage('git-checkout') {
        steps {
            git branch: 'main', url: 'https://github.com/chanduooo/deploy-nginx-.git'
        }
    }
        stage('Deploy to AWS') {
            steps {
                withAWS(credentials: 'aws-cred') {
                    sh '''
                    # Example AWS CLI command
                    aws s3 ls
                    '''
                    
                }
            }
        }
        
    }
}
