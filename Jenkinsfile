pipeline {
  agent any
  stages {
    stage('SonarQube') {
      agent any
      steps {
        script {
          stage 'Gradle Static Analysis'
          withSonarQubeEnv {
            sh "opt/sonar-scanner/bin/sonar-scanner" }
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