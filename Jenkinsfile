pipeline {
  agent any
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
  }
  stages {
	
    stage('Scan') {
      steps {
        withSonarQubeEnv(installationName: 'sq1') { 
          sh'./gradlew sonar'
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
