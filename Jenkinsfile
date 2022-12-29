pipeline {
  agent {
    node {
      label 'worker-03'
    }

  }
  stages {
    stage('get version') {
      steps {
        sh 'cat ./Quiz2-master/pom.xml | grep "*-SNAPSHOT"'
      }
    }

  }
  environment {
    node = 'worker'
  }
}