pipeline {
  agent any
  stages {
    stage('Start') {
      steps {
        sh 'echo \'hello from Pipeline\''
      }
    }
    stage('Test') {
      agent any
      steps {
        sh 'mvn install'
      }
    }
  }
}