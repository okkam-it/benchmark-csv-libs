pipeline {
  agent any
  stages {
    stage('Start') {
      steps {
        sh 'echo \'hello from Pipeline\''
      }
    }
    stage('Sonar') {
      parallel {
        stage('Sonar') {
          steps {
            waitForQualityGate()
          }
        }
        stage('SonarQube analysis') {
          steps {
            sh '''node {
              withSonarQubeEnv(\'My SonarQube Server\') {
                 sh \'mvn clean package sonar:sonar\'
              }
          }'''
            }
          }
          stage('Quality Gate') {
            steps {
              sh '''timeout(time: 1, unit: \'HOURS\') {
              def qg = waitForQualityGate()
              if (qg.status != \'OK\') {
                  error "Pipeline aborted due to quality gate failure: ${qg.status}"
              }
          }'''
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