pipeline {
  agent any
  stages {
    stage('Start') {
      steps {
        sh 'echo \'hello from Pipeline\''
      }
    }
    stage('Maven Install') {
      steps {
        sh 'sh \'mvn  install\''
      }
    }
  }
}