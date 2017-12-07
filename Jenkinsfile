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
      steps {
        sh 'verify -Prun-its,coverage'
      }
    }
  }
}