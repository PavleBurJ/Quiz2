pipeline {
    agent{label 'worker-03'}
    options { 
        buildDiscarder(logRotator(numToKeepStr: '5'))
        }
    stages {
        stage('run maven') {agent{label 'worker-03'}
        steps{
            print "run maven"
            sh '''  '''
            }
        }
        stage('check version') {agent{label 'worker-03'}
        steps{
            print "check version"
            sh 'cat /root/jenkins/workspace/BlueOcean_master/pom.xlm | grep "SNAPSHOT"'
            }
 }
  }
}
