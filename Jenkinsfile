pipeline {
    agent any
         tools {
                 maven 'Maven 3.6.3'
                 //jdk 'JDK7'

             }
    stages {
        stage('Checkout'){
            steps {
                 deleteDir()
                 sh 'sleep 60'
                 sh 'echo after deleteDir....'
                 checkout([
                     $class: 'GitSCM',
                     branches: [[name: '*/master/*']],
                     doGenerateSubmoduleConfigurations: false,
                     extensions: [[$class: 'CleanCheckout']],
                     submoduleCfg: [],
                     userRemoteConfigs: [[credentialsId: 'Azure-GIT-ID', url: 'https://maheshbadenehal@dev.azure.com/maheshbadenehal/MyFirstProject/_git/Sample1']]
                 ])
            }
        }
        stage('Build') {
            steps {
                sh 'echo Mahesh-From-Release1.1 on March 22 2020 Mahesh Babu Divya Tanvi Arjunn'
                //sh 'mvn --version'
                //sh 'mvn clean'
                sh 'mvn clean install'
            }
        }


    }
}
