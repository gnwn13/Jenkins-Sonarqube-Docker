pipeline {
  agent {
    node {
      label 'docker-slave'
    }
  }
  stages {
      stage('hello') {
          steps {
                  echo 'Hello'
            }
        }
      stage('SCM') {
          steps {
                checkout scm
            }
      }
      stage('SonarQube Analysis') {
          steps {
              def scannerHome = tool 'SonarScanner';
              withSonarQubeEnv() {
                  sh "${scannerHome}/bin/sonar-scanner"
              }
          }
      }
  }
}
