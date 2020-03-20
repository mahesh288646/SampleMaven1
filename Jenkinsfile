pipeline {
    agent any
         tools {
                 maven 'Maven 3.6.3'
                 //jdk 'JDK7'

             }
    stages {
        stage('Checkout'){
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                sh 'mvn --version'
                //sh 'mvn clean'
                sh 'mvn clean install'
            }
        }


    }
}
