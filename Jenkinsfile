#!/usr/bin/env groovy
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
            agent {
                label 'vms'
            }
            failFast true
            parallel {
                stage('mvn clean install in parallel') {                
                    steps {
                        echo "On Branch A"
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