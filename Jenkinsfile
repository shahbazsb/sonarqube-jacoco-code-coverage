pipeline {
  agent any
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
  }
   environment {
        SONAR_LOGIN_TOKEN = "squ_ce89947911c77ea8f0045cbe038e191b8ce355e0"
    }
   tools{
    gradle '6.9.4'
   }
  stages {
	
    stage('Scan') {
      steps {
        withSonarQubeEnv(installationName: 'sq1') { 
	sh 'gradle --version'		
        
        }
      }
    }
	
	stage('Quality Gate') {
      steps {
        waitForQualityGate abortPipeline: true
      }
    }
  }
}
