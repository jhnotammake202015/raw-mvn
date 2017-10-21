#!/usr/bin/env groovy
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
                sleep 1000 * 10
                echo 'Still testing...'
                sleep 1000 * 10
            }
         }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}