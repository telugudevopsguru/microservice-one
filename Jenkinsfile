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
        
    }
}
