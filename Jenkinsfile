pipeline {
  agent any
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
  }
  stages {
	stage('Source') {
      steps {
        git url: 'https://github.com/shahbazsb/sonarqube-jacoco-code-coverage.git'
        }
      }
    
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
