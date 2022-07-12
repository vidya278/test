pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
            checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/vidya278/test']]])            

          }
        }
        
        stage ("terraform init") {
            steps {
                sh ('terraform init') 
            }
        }
         stage ("terraform plan") {
            steps {
                withAWS(credentials: 'sam-jenkins-demo-credentials'){
                sh ('terraform plan')
                }
            }
        }
        
    }
}
