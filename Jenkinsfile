pipeline {
    agent {
        label{worker-03} {
            image 'maven:3-alpine'
            args '-v /root/.m2:/root/.m2'
        }
    }
    options {
        skipStagesAfterUnstable()
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('version') { 
            steps {
                sh 'cat /root/jenkins/workspace/BlueOcean_master/pom.xml | grep "SNAPSHOT"' 
            }
        }
    }
}
