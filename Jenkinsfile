pipeline {

  agent any

  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
  }
  environment {
    DOCKERHUB_CREDENTIALS_PSW = credentials('token-dockerhub')
    DOCKERHUB_CREDENTIALS_USR = 'yassineelbahi'
  }
  stages {
    stage('Build') {
      steps {
        sh './scripts/Build.sh'

      }
    }
    stage('Login') {
      steps {
        sh './scripts/Login.sh'

      }
    }
    stage('Push') {
      steps {
        sh './scripts/Push.sh'
      }
    }
  }
  post {
    always {
      sh './scripts/Logout.out'
    }
  }
}