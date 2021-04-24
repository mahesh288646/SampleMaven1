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
            echo "${application-name}"
            }
        }
        stage('Deploying-Dev') {
            steps {
                sh 'echo Mahesh-From-Release1.1 on March 22 2020 Mahesh Babu Divya Tanvi Arjunnnnnmmmmn'
                load ./AdminRepo/"${application-name}"/dev.groovy
                
		        script {
          kubernetesDeploy(configs: "**/manifests/${env.DB_URL2}/*", kubeconfigId: "mykubeconfig")
        }
            }
        }
        stage('Deploying-QA') {
            steps {
                sh 'echo Mahesh-From-Release1.1 on March 22 2020 Mahesh Babu Divya Tanvi Arjunnnnnmmmmn'
                load ./AdminRepo/"${application-name}"/qa.groovy
		        script {
          kubernetesDeploy(configs: "**/manifests/${env.DB_URL2}/*", kubeconfigId: "mykubeconfig")
        }
            }
        }
    }
}

