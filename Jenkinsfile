pipeline {
  agent {
    kubernetes {
      yamlFile 'pod-delete.yaml'
    }
  }
  // stages {
  //   stage('Setup ENVs') {
  //     steps {
  //       sh "echo EXPERIMENT NAME = ${EXPERIMENT_NAME}"
  //     }
  //   }
  // }
}
