pipeline {
  agent any
  stages {
    stage('SonarQube') {
      agent any
      steps {
        waitForQualityGate()
      }
    }
    stage('Maven Install') {
      steps {
        sh 'mvn install'
      }
    }
  }
}