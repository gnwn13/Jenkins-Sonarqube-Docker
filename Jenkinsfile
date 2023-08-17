// node {
//   stage('SonarQube analysis') {
//       environment {
//           SONAR_URL = "http://10.3.3.98:9000"
//       }
//       steps {
//          withCredentials([string(credentialsId: 'sonar-token', variable: 'SONAR_AUTH_TOKEN')]) {
//              def scannerHome = tool 'SonarScanner';
//              sh '${scannerHome}/bin/sonar-scanner -Dsonar.login=$SONAR_AUTH_TOKEN -Dsonar.host.url=${SONAR_URL} -Dsonar.projectKey=testing'
//              sh "${scannerHome}/bin/sonar-scanner"
//          }
//       }
//    }
// }

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
      // stage('Static Code Analysis') {
      //     environment {
      //       SONAR_URL = "http://10.3.3.98:9000"
      //     }
      //     steps {
      //       withCredentials([string(credentialsId: 'sonar-token', variable: 'SONAR_AUTH_TOKEN')]) {
      //         sh '/var/jenkins_home/tools/hudson.plugins.sonar.SonarRunnerInstallation/SonarScanner/bin/sonar-scanner -Dsonar.login=$SONAR_AUTH_TOKEN -Dsonar.host.url=${SONAR_URL} -Dsonar.projectKey=test-scan-project -Dsonar.projectBaseDir=/var/jenkins_home/workspace/test-project'
      //       }
      //     }
      // }
      stage('SonarQube analysis') {
          tools {
            sonarQube 'SonarQube Scanner for Jenkins 2.15'
            // sonarQube 'SonarScanner 5.0.1.3006'
          }
          steps {
            withSonarQubeEnv('SonarQube Scanner') {
              sh 'sonar-scanner'
            }
          }
      }
   }
}
