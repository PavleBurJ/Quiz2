pipeline {
  agent any
  stages {
    stage('get version') {
      steps {
        sh '''#!/bin/sh
value=`cat target/version.txt`
echo "$value"'''
      }
    }

  }
}