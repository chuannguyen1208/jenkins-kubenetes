pipeline {
  agent any

  stages {
    stage('Checkout Source') {
      steps {
        git 'https://github.com/chuannguyen1208/jenkins-kubenetes.git'
      }
    }

    stage('Deploy to k8s'){
      steps{
          script{
              kubernetesDeploy (configs: 'deployment.yaml')
          }
      }
    }
  }
}