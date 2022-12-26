pipeline {
  agent any
  stages {
    stage ('Build') {
      steps {
        sh 'printenv'
        
        }
    }
    stage ('Publish to ECR') {
      steps {
      withEnv(["AWS_ACCESS_KEY_ID=${env.AWS_ACCESS_KEY_ID}", "AWS_SECRET_ACCESS_KEY=${env.AWS_SECRET_ACCESS_KEY}", 
      "AWS_DEFAULT_REGION=${env.AWS_DEFAULT_REGION}"]) {
      sh 'docker login -u AWS -p $(aws ecr get-login-password --region us-east-1) 166480073310.dkr.ecr.us-east-1.amazonaws.com'
      sh 'docker build -t ecr-demo-push .'
      sh 'docker tag ecr-demo-push:latest public.ecr.aws/t9z5u5p5/ecr-push-demo:""$BUILD_ID""'
      sh 'docker push 166480073310.dkr.ecr.us-east-1.amazonaws.com/ecr-demo-push:latest:""$BUILD_ID""'
      }
  }
  }
  }
  }
