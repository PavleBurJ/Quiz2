pipeline {
    agent{label 'worker-03'}
    stages {
    stage ('Build') {
            steps {
                sh 'mvn clean install' 
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
