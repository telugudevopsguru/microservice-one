@Library('shared-library') _

pipeline {
    agent any
    tools{
maven 'Maven-3.9.6'
    }

    stages {
        stage('Git clone ') {
            steps {
                gitClone('main', 'github-credentials', 'https://github.com/telugudevopsguru/microservice-one.git')
            }
        }

        stage ('Build the Code'){
            steps{
            buildCode()
            }

        }

        stage('Build the Docker image') {
            steps {
                script {
                    dockerBuild('590184088314', 'us-east-1', 'microservice-one')
                }
            }
        }

        stage('Push to AWS ECR') {
            steps {
                script {
                    dockerImagePush('590184088314', 'us-east-1', 'microservice-one')
                }
            }
        } 

        
        
    }
}
