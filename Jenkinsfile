pipeline {
  agent {
    node {
      label ''
      name 'ec2-v1'
    }
  }
  stages {
    stage('Build Docker image') {
      steps {
        sh 'docker build -t yanir/docker-react -f Dockerfile.dev .'
      }
    }
    stage('Run tests') {
      steps {
        sh 'docker run yanir/docker-react npm run test -- --coverage'
      }
    }
    stage('Deploy to Elastic Beanstalk') {
      steps {
        withAWS(credentials: 'aws-credentials', region: 'eu-central-1') {
          sh 'pip install awscli'
          sh 'aws configure set aws_access_key_id $AWS_ACCESS_KEY'
          sh 'aws configure set aws_secret_access_key $AWS_SECRET_KEY'
          sh 'aws configure set default.region eu-central-1'
          sh 'aws elasticbeanstalk create-application-version --application-name docker --version-label $BUILD_NUMBER --source-bundle S3Bucket="elasticbeanstalk-eu-central-1-345543032218",S3Key="docker-path"'
          sh 'aws elasticbeanstalk update-environment --environment-name Docker-env --version-label $BUILD_NUMBER'
        }
      }
    }
  }
}
