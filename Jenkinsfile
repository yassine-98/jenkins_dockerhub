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
        sh './Build.sh'

      }
    }
    stage('Login') {
      steps {
        sh './Login.sh'

      }
    }
    stage('Push') {
      steps {
        sh './Push.sh'
      }
    }
  }
  post {
    always {
      sh './Logout.out'
    }
  }
}