pipeline {
   agent any
   stages {
        stage('Checkout') {
            steps {
                git clone https://github.com/PavleBurJ/Quiz2.git
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'jenkins-user-github', url: 'https://github.com/aakashsehgal/FMU.git']]])
                sh "ls -lart ./*"
            }
        }     
    }
}
