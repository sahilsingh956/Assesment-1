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
                withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AKIAXLOIG5PCMQUDKT4B', credentialsId: 'asw-creds', secretKeyVariable: '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']])
                {
                    sh 'aws cloudformation create-stack --stack-name my-s3-bucket --region ap-south-1 --template-body file://Task1.yml'
                }
              }
            }
        }
    }
