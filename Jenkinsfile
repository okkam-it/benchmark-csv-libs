pipeline {
  agent any
  stages {
    stage('Start') {
      steps {
        sh 'echo \'hello from Pipeline\''
      }
    }
    stage('SonarQube') {
      parallel {
        stage('SonarQube') {
          steps {
            waitForQualityGate()
          }
        }
        stage('Test') {
          steps {
            script {
              withSonarQubeEnv('SonarQube') {
                sh "../../../sonar-scanner-2.9.0.670/bin/sonar-scanner"
              }
            }
            
          }
        }
      }
    }
  }
}