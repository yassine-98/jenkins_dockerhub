pipeline {

  agent any
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
  }
  environment {
    DOCKERHUB_CREDENTIALS = credentials('token-dockerhub')
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
        sh 'docker login'
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