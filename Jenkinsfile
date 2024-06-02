@Library('shared-library') _

pipeline {
    agent any

    stages {
        stage('Git clone ') {
            steps {
                gitClone('main', 'github-credentials', 'https://github.com/telugudevopsguru/microservice-one.git')
            }
        }

        stage ('Build the Code'){
            buildCode()

        }
        
    }
}
