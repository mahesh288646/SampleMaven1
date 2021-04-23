pipeline {
    agent any
         tools {
                 maven 'Maven'
                 //jdk 'JDK7'

             }
    stages {
        stage('Checkout'){
            steps {
                 deleteDir()

                 sh 'echo after deleteDir....'
checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/mahesh288646/SampleMaven1.git']]])
            }
        }
        stage('Build') {
            steps {
                sh 'echo Mahesh-From-Release1.1 on March 22 2020 Mahesh Babu Divya Tanvi Arjunnnnnmmmmn'
                load 'staging.groovy'
		        withKubeConfig([credentialsId: 'kube1', serverUrl: 'http://ec2-100-25-220-44.compute-1.amazonaws.com:6443']) {
      sh 'kubectl get pods -A'
    }

}
		//sh 'mvn --version'
                //sh 'mvn clean'
                //sh 'mvn clean install'
            }
        }


    }
}
