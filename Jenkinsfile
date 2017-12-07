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
        }
      }
      stage('End') {
        steps {
          echo 'End'
        }
      }
    }
  }