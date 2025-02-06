pipeline {
  agent any
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
  }
   environment {
        
        SONAR_LOGIN_TOKEN = "squ_ce89947911c77ea8f0045cbe038e191b8ce355e0"
        
    }
  stages {
	
    stage('Scan') {
      steps {
        withSonarQubeEnv(installationName: 'sq1') { 
          sh "./gradlew sonar -Dsonar.login='${SONAR_LOGIN_TOKEN}' --no-daemon --watch-fs --build-cache --info"
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
