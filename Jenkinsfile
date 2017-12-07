pipeline {
  agent any
  stages {
    stage('SonarQube') {
      agent any
      steps {
        script {
          stage 'Gradle Static Analysis'
          withSonarQubeEnv {
            sh "op/sonarqube-scanner/bin/sonar-scanner" }
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