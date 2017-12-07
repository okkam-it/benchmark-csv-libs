pipeline {
  agent any
  stages {
    stage('SonarQube') {
      parallel {
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
          stage('scri') {
            steps {
              sh '                sh "mvn sonar:sonar -Dsonar.host.url=${env.SONARQUBE_HOST}"'
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