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
    stage('Test Sonar') {
      steps {
        sh 'mvn sonar:sonar'
      }
    }
  }
}