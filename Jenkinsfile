pipeline {
    agent {label 'worker-03'}
    stages {
        stage('determine maven version') {agent{label 'worker-03'}
        steps{
            print "maven version"
            sh '''
cat pom.xml | grep "^    <version>.*</version>$" | awk -F'[><]' '{print $3}'
'''
            }
        }
}
}
}
