pipeline {
  agent {
    kubernetes {
      yamlFile 'pod-delete.yaml'
    }
  }
  stages {
    stage('Setup ENVs') {
      steps {
        sh 'set'
        sh "echo INSTALL_LITMUS = ${INSTALL_LITMUS}"
        sh "echo EXPERIMENT NAME = ${EXPERIMENT_NAME}"
        container('pod-delete') {
          sh 'export EXPERIMENT_NAME =pod-delete'
        }
      }
    }
  }
}
