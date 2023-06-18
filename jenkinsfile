pipeline {
  agent any
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
  }
  environment {
    DOCKERHUB_CREDENTIALS = credentials('edwardeddie10/jenkins-docker/')
  }
  stages {
    stage('Build') {
      steps {
        sh 'docker build -t edwardedde10/jenkins-docker-hub .'
      }
    }
    stage('Login') {
      steps {
        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
      }
    }
    stage('Push') {
      steps {
        sh 'docker push edwardedde10/jenkins-docker-hub'
      }g
    }
  }
  post {
    always {
      sh 'docker logout'
    }
  }
}