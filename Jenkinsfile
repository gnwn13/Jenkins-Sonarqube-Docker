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
      stage('Static Code Analysis') {
          environment {
            SONAR_URL = "http://10.3.3.98:9000"
          }
          steps {
            withCredentials([string(credentialsId: 'sonar-token', variable: 'SONAR_AUTH_TOKEN')]) {
              sh 'SonarScanner/bin/sonar-scanner -Dsonar.login=$SONAR_AUTH_TOKEN -Dsonar.host.url=${SONAR_URL}' -Dsonar.projectKey=test-scan-project -Dsonar.projectBaseDir=/var/jenkins_home/workspace/test-project
            }
          }
      }
      // stage('SonarQube Analysis') {
      //     steps {
      //         def scannerHome = tool 'SonarScanner';
      //         withSonarQubeEnv() {
      //             sh "${scannerHome}/bin/sonar-scanner"
      //         }
      //     }
      // }
  }
}
