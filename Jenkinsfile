@Library('shared-library') _

pipeline {
    agent any
    tools {
        maven 'Maven-3.9.6'
    }
    
    parameters {
        string(name: 'branchName', defaultValue: 'main', description: 'Branch name')
		string(name: 'ecrRepoName', defaultValue: 'microservice-one', description: 'ecrRepoName')
		string(name: 'accountNumber', defaultValue: '590184088314', description: 'accountNumber')
        choice(name: 'region', choices: ['us-east-1','us-west-2'], description: 'Select AWS region')
    }
    
    stages {
        stage('Clone the repo') {
            steps {
                script {
                    gitClone(params.branchName, 'github-credentials', 'https://github.com/telugudevopsguru/microservice-one.git')
                }
            }
        }
        stage('Build Code') {
            steps {
                buildCode()
            }
        }
        
        stage('Build and Tag Docker Image') {
            steps {
                script {
                    dockerBuild(params.accountNumber, params.region, params.ecrRepoName)
                }
            }
        }
       
        stage('Push to ECR') {
            steps {
                script {
                    dockerImagePush(params.accountNumber, params.region, params.ecrRepoName)
                }
            }
        } 
    }
}
