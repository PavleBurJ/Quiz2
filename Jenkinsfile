pipeline {
  agent {
    node {
      label 'worker-02'
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