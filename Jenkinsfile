pipeline {
  agent {
    node {
      label 'worker-02'
    }

  }
  stages {
    stage('pull') {
      steps {
        git(url: 'https://github.com/PavleBurJ/Quiz2.git', branch: 'master')
      }
    }

    stage('get version') {
      steps {
        sh 'cat pom.xml | grep "*-SNAPSHOT"'
      }
    }

  }
  environment {
    node = 'worker'
  }
}