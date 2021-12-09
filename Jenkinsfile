pipeline {
  agent {
    kubernetes {
      yamlFile 'pod-delete.yaml'
    }
  }
  stages {
    stage('Show Experiment') {
      steps {
        container('jnlp') {
          sh "echo running pod-delete experiment"
        }
      }
    }
  }
}
