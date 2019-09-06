pipeline {

    agent {
        docker {
            image 'obe.artifactory.gscorp.ad/snapshot/obe-builder:1.3.0'
            args '-v /var/lib/jenkins/.m2:/home/obe-developer/.m2 -eMAVEN_OPTS="-Dfile.encoding=UTF-8"'
        }
    }

    stages {

        stage('Clone repo') {
            steps{
                checkout([$class: 'GitSCM', branches: [[name: 'refs/heads/master']], doGenerateSubmoduleConfigurations: false, extensions: [[$class: 'CleanBeforeCheckout']], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/nicopaez/serenity-cucumber4-starter.git']]])
            }
        }

        stage('Aceptación') {
                stage('Aceptación team 1') {
                    steps{
                        sh "mvn verify"
                    }
                }
        }

    }
}
