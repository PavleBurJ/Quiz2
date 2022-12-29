pipeline {
  agent any
  stages {
    stage('get version') {
      steps {
        sh '''#!/bin/sh
value=`cat Quiz2/blob/master/pom.xml`
echo $version'''
      }
    }

  }
}