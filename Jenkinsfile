pipeline {
  agent {
    node {
      label 'worker-03'
    }

  }
  stages {
    stage('get version') {
      steps {
        sh 'find .'
      }
    }

  }
  environment {
    node = 'worker'
  }
}