pipeline {
    agent any
         tools {
                 maven 'Maven'
                 //jdk 'JDK7'

             }
    stages {
        stage('Checkout from AdminRepo'){
            steps {
                 sh 'echo after deleteDir....'
                 dir('AdminRepo') {
                 checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/mahesh288646/Admin_REPO.git']]])
                                  }
                  }
                                   }
        stage('Checkout from Application Repo'){
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/mahesh288646/SampleMaven1.git']]])
                load "application.properties"
                  }
        }
        stage('Deploying-Dev') {
            steps {
                load "./AdminRepo/${application_name}/dev/dev_crazy.txt"
                sh "mkdir dev qa manifests && cp deployment.yaml ./dev && cp deployment.yaml ./qa"
                sh "sed -i 's/application_name/${application_name}/g' ./manifests/dev/deployment.yaml"
                sh "sed -i 's/replicas_count/${replicas}/g' ./manifests/dev/deployment.yaml"
                script {
                    kubernetesDeploy(configs: "**/manifests/${environment}/*", kubeconfigId: "mykubeconfig")
                        }
                 }
                                }
        stage('Deploying-QA') {
            steps {
                load "./AdminRepo/${application_name}/qa/qa_crazy.txt"
                sh "sed -i 's/application_name/${application_name}/g' ./manifests/qa/deployment.yaml"
                sh "sed -i 's/replicas_count/${replicas}/g' ./manifests/qa/deployment.yaml"
		        script {
                    kubernetesDeploy(configs: "**/manifests/${environment}/*", kubeconfigId: "mykubeconfig")
                        }
                }
                                }
    }
}