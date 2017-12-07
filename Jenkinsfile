pipeline {
  agent any
  stages {
    stage('Start') {
      steps {
        sh 'echo \'hello from Pipeline\''
      }
    }
    stage('SonarQube analysis') {
      steps {
        script {
          stage("SonarQube analysis") {
            node {
              withSonarQubeEnv('My SonarQube Server') {
                sh 'mvn clean package sonar:sonar'
              }
            }
          }
        }
        
      }
    }
    stage('End') {
      steps {
        echo 'End'
      }
    }
  }
}