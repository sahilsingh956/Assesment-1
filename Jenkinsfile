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
                withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AKIAXLOIG5PCM2G6UFWF', credentialsId: 'aws-creds', secretKeyVariable: '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']])
                {
                    sh 'aws cloudformation create-stack --stack-name my-s3-bucket --region ap-south-1 --template-body file://Task1.yml'
                }
              }
            }
        }
    }
