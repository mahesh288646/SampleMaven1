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

                 sh 'echo after deleteDir....'
                 checkout([
                     $class: 'GitSCM',
                     branches: [[name: '*/master/*']],
                     doGenerateSubmoduleConfigurations: false,
                     extensions: [[$class: 'CleanCheckout']],
                     submoduleCfg: [],
                     userRemoteConfigs: [[credentialsId: 'Git-ID', url: 'https://github.com/mahesh288646/SampleMaven1.git']]
                 ])
            }
        }
        stage('Build') {
            steps {
                sh 'echo Mahesh-From-Release1.1 on March 22 2020 Mahesh'
                //sh 'mvn --version'
                //sh 'mvn clean'
                sh 'mvn clean install'
            }
        }


    }
}
