pipeline {
    agent {label 'worker-03'}
    stages {
        stage('determine maven version') {agent{label 'worker-03'}
        steps{
            print "maven version"
            sh '''
cat /root/jenkins/workspace/BlueOcean_master/pom.xml | grep "SNAPSHOT"
'''
            }
        }
        stage('Build') {
          steps {
            sh 'mvn -Dmaven.test.failure.ignore=true install'
          }
          post {
            success {
              junit 'target/surefire-reports/**/*.xml'
            }
          }
        }
}
}
