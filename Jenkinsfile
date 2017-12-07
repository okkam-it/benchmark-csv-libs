pipeline {
  agent any
  stages {
    stage('Test Java') {
      steps {
        sh 'java -version'
        sh 'which java'
      }
    }
    stage('Test Maven') {
      steps {
        sh 'mvn -version'
        sh 'which mvn'
      }
    }
    stage('Test Coverage') {
      agent any
      steps {
        sh 'scannerHome = tool \'SonarQubeaScanner\'; echo ${scannerHome}'
        script {
          withSonarQubeEnv('SonarQube-6.7') {
            sh "opt/bin/sonar-scanner"
          }
        }
        
      }
    }
  }
}