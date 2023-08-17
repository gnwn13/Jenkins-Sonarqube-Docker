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
      stage('SonarQube Analysis') {
          steps {
              script {
                  def scannerHome = tool 'SonarScanner'; // Name of the SonarQube Scanner you created in "Global Tool Configuration" section
                  withSonarQubeEnv() {
                      sh "${scannerHome}/bin/sonar-scanner"
                  }
              }
          }
      }
   }
}
