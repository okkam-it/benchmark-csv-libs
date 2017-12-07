pipeline {
  agent any
  stages {
    stage('Start') {
      steps {
        sh 'echo \'hello from Pipeline\''
      }
    }
    stage('SonarQube') {
      steps {
        waitForQualityGate()
        script {
          withSonarQubeEnv('My SonarQube Server') {
            sh 'mvn clean package sonar:sonar'
          }
        }
        
        script {
          timeout(time: 1, unit: 'HOURS') {
            def qg = waitForQualityGate()
            if (qg.status != 'OK') {
              error "Pipeline aborted due to quality gate failure: ${qg.status}"
            }
          }
        }
        
      }
    }
  }
}