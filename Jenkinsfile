pipeline {
  agent any
  stages {
    stage('Start') {
      steps {
        sh 'echo \'hello from Pipeline\''
      }
    }
    stage('SonarQube analysis') {
      parallel {
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
        stage('Quality Gate') {
          steps {
            script {
              stage("Quality Gate"){
                timeout(time: 1, unit: 'HOURS') {
                  def qg = waitForQualityGate()
                  if (qg.status != 'OK') {
                    error "Pipeline aborted due to quality gate failure: ${qg.status}"
                  }
                }
              }
            }
            
          }
        }
      }
    }
    stage('Maven Install') {
      steps {
        sh 'sh \'mvn  install\''
      }
    }
  }
}