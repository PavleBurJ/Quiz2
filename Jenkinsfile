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
        stage('run maven') {agent{label 'worker-03'}
        steps{
            print "run maven"
            sh '''
sh 'mvn -B -DskipTests clean package'
'''
            }
        }
}
}
