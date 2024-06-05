pipeline {
    agent any
    environment {
        AWS_CREDENTIALS_ID = 'aws-cred' // Replace with your actual credentials ID
    }
    stages {
        stage('git-checkout') {
        steps {
            git branch: 'main', url: 'https://github.com/chanduooo/deploy-nginx-.git'
        }
    }
        stage('Deploy to AWS') {
            steps {
                script {
                    withAWS(credentials: "${AWS_CREDENTIALS_ID}", region: 'us-east-2') {
                        sh 'aws s3 ls'
                    }
                }
            }
    }
}
}
