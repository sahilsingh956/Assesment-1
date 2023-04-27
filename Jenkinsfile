pipeline {
    agent any
    stages {
        stage('Checkout from git'){
            steps {
                    checkout changelog: false, poll: false, scm: scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/sahilsingh956/Assesment-1.git']])
                   }
            }
        stage('Create S3 bucket') {
            steps {
                    sh 'aws cloudformation create-stack --stack-name my-s3-bucket --template-body file://Task1.yml'
                }
            }
        }
    }
