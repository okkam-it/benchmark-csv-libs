pipeline {
  agent any
  stages {
    stage('SonarQube') {
      agent any
      steps {
        script {
          stage 'Checkout'
          
          checkout scm
          
          stage 'Gradle Static Analysis'
          withSonarQubeEnv {
            sh "./gradlew clean sonarqube"
          }
          
        }
        
      }
    }
    stage('Maven Install') {
      steps {
        sh 'mvn install'
      }
    }
  }
}