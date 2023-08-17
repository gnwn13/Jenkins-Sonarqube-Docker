pipeline {
  agent {
    node {
      label 'docker-slave'
    }
  }
  stages {
    stage('hello') {
      echo 'Hello World'
    }
    stage('SCM') {
      checkout scm
    }
    stage('SonarQube Analysis') {
      def scannerHome = tool 'SonarScanner';
      withSonarQubeEnv() {
        sh "${scannerHome}/bin/sonar-scanner"
      }
    }
  }
}
