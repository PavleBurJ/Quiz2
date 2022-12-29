pipeline {
  agent any
  stages {
    stage('get version') {
      steps {
        sh '''#!/bin/sh
value=`cat blob/master/pom.xml`
echo $version'''
      }
    }

  }
}