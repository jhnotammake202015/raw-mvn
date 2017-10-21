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
            steps {
                echo 'Building..'
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
            echo "with failure - ${currentBuild.result} | ${currentBuild.description}"
        }
    }
}