pipeline {
  agent any
  stages {
    stage('get version') {
      steps {
        sh '''#!/bin/sh
cat pom.xml | grep "<version>*-SNAPSHOT</version>"'''
      }
    }

  }
}