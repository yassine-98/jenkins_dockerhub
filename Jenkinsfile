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
        sh 'docker build -t yassineelbahi/hub-alpine:latest .'
        sh ' env | sort'
      }
    }
    stage('Login') {
      steps {
        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'

      }
    }
    stage('Push') {
      steps {
        sh 'docker push yassineelbahi/hub-alpine:latest'
      }
    }
  }
  post {
    always {
      sh 'docker logout'
    }
  }
}