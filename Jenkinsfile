pipeline {
  agent any
  stages {
    stage('Test Java') {
      steps {
        sh 'java -version'
        sh 'which java'
      }
    }
    stage('Test Maven') {
      steps {
        sh 'mvn -version'
        sh 'which mvn'
        sh 'mvn install'
      }
    }
    stage('Test Coverage') {
      agent any
      steps {
        sh '''echo "Script executed from: ${PWD}"
'''
        script {
          withSonarQubeEnv('SonarQube-6.7') {mvn sonar:sonar}
        }
        
      }
    }
  }
}