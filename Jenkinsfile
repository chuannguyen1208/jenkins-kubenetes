pipeline {
  agent {
    kubernetes {
      yaml '''
        apiVersion: v1
        kind: Pod
        spec:
          containers:
          - name: jnlp
            image: 'jenkins/inbound-agent'
      '''
    }
  }
  stages {
    stage('Run maven') {
      steps {
        container('jnlp') {
          sh 'echo Hello'
        }
      }
    }
  }
}