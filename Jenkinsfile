pipeline {
    agent{label 'worker-03'}
    tools { 
        maven 'Maven 3.3.9' 
        jdk 'jdk8' 
    }
    options { 
        buildDiscarder(logRotator(numToKeepStr: '5'))
        }
        stage ('Build') {
            steps {
                sh 'mvn -Dmaven.test.failure.ignore=true install' 
            }
        stage('check version') {agent{label 'worker-03'}
        steps{
            print "check version"
            sh 'cat /root/jenkins/workspace/BlueOcean_master/pom.xlm | grep "SNAPSHOT"'
            }
 }
  }
}
