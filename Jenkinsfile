pipeline {
    agent any
         tools {
                 maven 'Maven'
                 //jdk 'JDK7'

             }
    stages {
        stage('Checkout-AdminRepo'){
            steps {
                 

                 sh 'echo after deleteDir....'
                 dir('AdminRepo') {
                 checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/mahesh288646/Admin_REPO.git']]])
                 sh 'ls -lrt'
                 sh 'pwd'
                 }
            }
        }
        stage('Checkout'){
            steps {
                 

                 sh 'echo after deleteDir....'
checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/mahesh288646/SampleMaven1.git']]])
            }
        }
        stage('Deploying-Dev') {
            steps {
                sh 'echo Mahesh-From-Release1.1 on March 22 2020 Mahesh Babu Divya Tanvi Arjunnnnnmmmmn'
                load 'dev.groovy'
		        script {
          kubernetesDeploy(configs: "**//$JOB_NAME/${env.DB_URL2}/*", kubeconfigId: "mykubeconfig")
        }
            }
        }
        stage('Deploying-QA') {
            steps {
                sh 'echo Mahesh-From-Release1.1 on March 22 2020 Mahesh Babu Divya Tanvi Arjunnnnnmmmmn'
                load 'qa.groovy'
		        script {
          kubernetesDeploy(configs: "**/${env.DB_URL2}/*", kubeconfigId: "mykubeconfig")
        }
            }
        }
    }
}

