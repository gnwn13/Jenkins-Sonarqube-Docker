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
      steps {
          script {
              def scannerHome = tool 'Sonar-Server'; // Name of the SonarQube Scanner you created in "Global Tool Configuration" section
              withSonarQubeEnv() {
                  sh "${scannerHome}/bin/sonar-scanner"
              }
          }
      }
   }
}
