#!/usr/bin/env groovy

def header(label) {
    echo label
}


pipeline {
    agent any
    stages {
        stage('Init'){
            steps {
                echo "Running ${env.BUILD_ID}, number ${env.BUILD_NUMBER} - ${env.BUILD_DISPLAY_NAME}"
                echo sh(script: 'env|sort', returnStdout: true)
            }
        }

        stage('Build') {
            failFast true
            parallel {
                stage('mvn clean install in parallel') {       
                    agent {
                        label 'vms'
                    }        
                    steps {
                        header("Running in vms slaves...h")
                        sh 'uname -a'
                    }
                }            
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
         }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }

    post {
        always {
            echo "Finished"
        }
            
        failure {  
            echo "with failure! ${currentBuild.result} | ${currentBuild.description}"
        }

        success {
            echo "Successful!"
        }

        unstable{
            echo "Unstable! ${currentBuild.result} | ${currentBuild.description}"
        }

        aborted{
            echo "Aborted! ${currentBuild.result} | ${currentBuild.description}"
        }
    }
}