pipeline {
    agent none
    environment {
       HOME = '/opt/API/PayCallback'
       API_DLL = 'Callback.API.dll'
       SWAG_PORT = '5001'
       GOLD_CONF_PATH = '/opt/configs/Test/Test-02/API/PayCallback'
       SRVC_NAME = 'PayCallback.API.service'
       SRVC_DNS = 'paycallback.02.test.api.lb.ge'
       ZIP_PASSWORD = credentials('TestEnvZipPass')
   }
    options { 
        skipDefaultCheckout()
        }
    stages {
        stage('Get-Scripts') {agent{label 'TestEnvironment'}
        steps{
            git branch: 'master',
                credentialsId: 'JenkinsDomainUser',
                url: 'http://tfs.lb.ge:8080/tfs/ITCollection/_git/DevOps'
            stash allowEmpty: true, includes: 'Scripts/B6Application/Check-Files-B6TS-FS.ps1', name: 'Stash-Check-Files-B6TS-FS'
            stash allowEmpty: true, includes: 'Scripts/B6Application/B6SRV-Service-Restart.ps1', name: 'B6SRV-Service-Restart'
            stash allowEmpty: true, includes: 'Scripts/B6Application/Check-Files-B6TS-FS.ps1', name: 'Stash-Check-Files-B6TS-FS'
            stash allowEmpty: true, includes: 'Scripts/B6Application/B6SRV-Service-Restart.ps1', name: 'B6SRV-Service-Restart'
            stash allowEmpty: true, includes: 'Scripts/B6Application/B6SRV-Service-Restart.ps1', name: 'B6SRV-Service-Restart'
            cleanWs()
            }
    }
        stage('Create Deploy.7z') {agent{label 'LinuxApp-Test-02.lb.ge'}
        steps{
            print "Unzip-CopyGoldConfig-Zip"
            copyArtifacts filter: 'target.zip', fingerprintArtifacts: true, flatten: true, projectName: 'Test/Test-02/API/Pay.ge/PayCallback.API/Build', target: '.\\'
            sh './Scripts/Unzip-With-Golds.sh'
            }
        }
        stage('Check Build Health') {agent{label 'LinuxApp-Test-02.lb.ge'}
        steps{
            print "ბილდის სტაბილურობის შემოწმება"
            sh './Scripts/Curl-Localhost-API.sh'
            }
        post {
            failure {
                cleanWs()
                sh 'rm -rf $HOME/JenkinsPath'
                error "Build Is Not Valid!"
            }
            success {
                echo "Build Is Valid!"
                }
            }
        }
        stage('Update API') {agent{label 'LinuxApp-Test-02.lb.ge'}
        steps{
            print "განახლების გადატანა"
            sh './Scripts/Update-API.sh'
            }
        }
        stage('API HealthCheck') {agent{label 'LinuxApp-Test-02.lb.ge'}
        steps{
            print "გადატანილი განახლების შემოწმება"
            sh './Scripts/Curl-DNS-API.sh'
            }
        post {
            failure {
                sh './Scripts/Rollback-API.sh'
                cleanWs()
                error "API RollBacked"
            }
            success {
                sh 'rm -rf $HOME/StableVersion'
                print "Deploy Succsessful"
                sh '''
                zip -q -P $ZIP_PASSWORD Current.zip ./* 
                '''
                archiveArtifacts artifacts: 'Current.zip', followSymlinks: false
                cleanWs()
                }
            }
        }
    }
}
