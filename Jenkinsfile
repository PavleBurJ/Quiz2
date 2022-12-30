pipeline {
    agent none
    options { 
        skipDefaultCheckout()
        buildDiscarder(logRotator(numToKeepStr: '5'))
        }
    stages {
        stage('determine maven version') {agent{label 'worker-02'}
        steps{
            print "maven version"
            sh '''
cat pom.xml | grep "^    <version>.*</version>$" | awk -F'[><]' '{print $3}'
'''
            }
        }
}
