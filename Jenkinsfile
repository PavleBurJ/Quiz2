pipeline {
    agent {
        docker {
            image 'maven:3-alpine'
            args '-v /root/.m2:/root/.m2'
        }
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
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage('check version') {agent{label 'docker'}
        steps{
            print "check version"
            sh 'cat /root/jenkins/workspace/Quiz2/pom.xlm | grep "SNAPSHOT"'
            }
 }
    }
}
