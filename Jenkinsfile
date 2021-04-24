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
            load 'application.properties'
            echo "$application_name"
            }
        }
        stage('Deploying-Dev') {
            steps {
                sh 'echo Mahesh-From-Release1.1 on March 22 2020 Mahesh Babu Divya Tanvi Arjunnnnnmmmmn'
                //def app_environment = "./AdminRepo/$application_name/dev/dev_crazy.txt"
                load "./AdminRepo/$environment/dev/dev_crazy.txt"
                echo "$environment"
		        script {
          kubernetesDeploy(configs: "**/manifests/${environment}/*", kubeconfigId: "mykubeconfig")
        }
            }
        }
        stage('Deploying-QA') {
            steps {
                sh 'echo Mahesh-From-Release1.1 on March 22 2020 Mahesh Babu Divya Tanvi Arjunnnnnmmmmn'
                load './AdminRepo/crazy/qa/qa_crazy.txt'
		        script {
          kubernetesDeploy(configs: "**/manifests/${environment}/*", kubeconfigId: "mykubeconfig")
        }
            }
        }
    }
}

