pipeline {
  agent any

  stages {
    stage('Checkout Source') {
      steps {
        git 'https://github.com/chuannguyen1208/jenkins-kubenetes.git'
      }
    }

    stage('Deploy to k8s'){
      steps {
        withKubeConfig(
        [
            credentialsId: 'jenkins-kind', 
            serverUrl: 'https://kubernetes.docker.internal:6443',
        ]) {
          sh 'kubectl version'
        }
      }
    }
  }
}