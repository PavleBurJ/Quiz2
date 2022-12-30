pipeline {
    agent{label 'worker-03'}
        tools {
        maven '$mavenHome'
        jdk '$JavaHome'
    }
    stages {
    stage ('Build') {
            steps {
                sh 'mvn -f /root/jenkins/workspace/BlueOcean_master/pom.xml clean install' 
            }
    }
        stage('check version') {agent{label 'worker-03'}
        steps{
            print "check version"
            sh 'cat /root/jenkins/workspace/BlueOcean_master/pom.xlm | grep "SNAPSHOT"'
            }
 }
                    post {
                success {
                    echo 'Now Archiving'
                }
            }
  }
}
