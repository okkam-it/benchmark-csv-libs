pipeline {
  agent any
  stages {
    stage('Start') {
      steps {
        sh 'echo \'hello from Pipeline\''
      }
    }
    stage('Sonar') {
      steps {
        waitForQualityGate()
      }
    }
    stage('End') {
      steps {
        echo 'End'
      }
    }
  }
}