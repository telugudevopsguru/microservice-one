pipeline {
    agent any
    triggers {
     // Job will run every five minutes, whether made changes in code or not. 
   cron('H/5 * * * *')
        
    }
    options {
        buildDiscarder(logRotator(numToKeepStr: '10'))
           disableConcurrentBuilds()
          timestamps()
    }
    
  


    tools{
        maven "Maven-3.9.6"
    }

    stages {
        stage('Clone the repository ') {
            steps {
              git branch: 'main', credentialsId: 'Github_credentails', url: 'https://github.com/MooleMuraliDharaReddy/java-app.git'
            }
        }
        
        
         stage('Build the code ') {
            steps {
              sh 'mvn clean install'
            }
        }
        
        
        stage('Deploy the war file in tomcat ') {
            steps {
           deploy adapters: [tomcat9(credentialsId: 'Tomcat-credentails', path: '', url: 'http://3.84.95.96:8080')], contextPath: null, war: '**/*.war'
            }
        }
        
    }
    post{

always{
echo ' Congratulations. Successfully run the jenkins job. '
}

}
    
}
