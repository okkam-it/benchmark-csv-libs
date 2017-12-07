pipeline {
  agent any
  stages {
    stage('SonarQube') {
      agent any
      steps {
        sh 'scannerHome = tool \'SonarQube Scanner 2.8\''
        sh '''withSonarQubeEnv(\'SonarQube Scanner\') {
          sh "${scannerHome}/bin/sonar-scanner"
        }'''
        }
      }
      stage('Maven Install') {
        steps {
          sh 'mvn install'
        }
      }
    }
  }