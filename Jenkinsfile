pipeline {

  environment {
    dockerimagename = "chuannt11673/jenkins.angular"
    dockerImage = ""
  }

  agent {
    docker {
      image 'jenkins/agent:latest'
    }
  }

  stages {

    stage('Checkout Source') {
      steps {
        git 'https://github.com/chuannguyen1208/jenkins-kubenetes.git'
      }
    }

    stage('Build image') {
      steps{
        script {
          dockerImage = docker.build dockerimagename
        }
      }
    }

    stage('Pushing Image') {
      environment {
               registryCredential = 'docker-credentials'
           }
      steps{
        script {
          docker.withRegistry( 'https://registry.hub.docker.com', registryCredential ) {
            dockerImage.push("latest")
          }
        }
      }
    }

    stage('Deploying container to Kubernetes') {
      steps {
        sh 'kubectl apply -f deployment.yaml'
      }
    }

  }

}