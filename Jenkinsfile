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
        script {
          withSonarQubeEnv('SonarQube-6.7') {
            pwd; sh "/opt/bin/sonar-scanner"
          }
        }
        
      }
    }
  }
}