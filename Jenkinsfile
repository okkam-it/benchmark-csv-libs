pipeline {
  agent any
  stages {
    stage('SonarQube') {
      agent any
      steps {
        script {
          stage 'Gradle Static Analysis'
          withSonarQubeEnv { def scannerHome = tool 'SonarQube Scanner 2.8';
          withSonarQubeEnv('My SonarQube Server'){
            sh "${scannerHome}/bin/sonar-scanner"}          }
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