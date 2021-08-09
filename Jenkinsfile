pipeline {
    agent any
    
    tools {
        go 'golang-1.15'
    }
    
    environment {
        GO111MODULE = 'off'
    }
    
    stages {
        stage('Golang Environment Check') {
            steps {
                sh 'go version';
                sh "echo ${GO111MODULE}";
            
            }
            
        }
         stage('SourceCode_Git') {
            steps {
                 git 'https://github.com/irezaul/testweb1.git'
            }
        }
         stage('Build') {
            steps {
                sh 'go build'
            }
        }
        
         stage('Execute_permission') {
            steps {
                sh '''chmod +x ./GoWebAppPipline'''
            }
        }
        stage('Service_done') {
            steps {
                //sh './GoWebAppPipline'
            }
        }
         stage('Release') {
            steps {
                echo 'Reeasing....'
            }
            post {
               
                always {
                    
                    mail to: "mtmartadd@gmail.com", subject:"${currentBuild.currentResult}: ${currentBuild.fullDisplayName}", body: "Test passed."
                }
            }
        }
        
        
    }
}
