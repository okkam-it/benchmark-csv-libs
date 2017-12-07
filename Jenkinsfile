pipeline {
  agent any
  stages {
    stage('Tools Setup') {
      steps {
        script {
          tools {
            jdk 'jdk7'
            maven 'maven3'
          }
        }
        
      }
    }
    stage('Test Java') {
      steps {
        sh 'sh \'java -version\''
        sh 'sh \'which java\''
      }
    }
  }
}