pipeline {
  agent {
    kubernetes {
      yamlFile 'pod-delete.yaml'
    }
  }
  stages {
    stage('Show ENVs') {
      steps {
        container('jnlp') {
          sh "echo hello world"
        }
      }
    }
  }
}
