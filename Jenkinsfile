pipeline {
  agent any
  stages {
    stage('get version') {
      steps {
        sh 'cat pom.xml | grep "^    <version>.*</version>$" | awk -F\'[><]\' \'{print $3}\''
      }
    }

  }
}