pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        checkout scm
        sh 'ls -la'
      }
    }

    stage('Build Docker Image') {
      steps {
        sh 'docker --version'
        sh 'docker build -t flask-hello:latest .'
      }
    }

    stage('Run Container') {
      steps {
        sh '''
          docker rm -f flask-hello || true
          docker run -d --name flask-hello -p 8082:5000 flask-hello:latest
          docker ps --filter "name=flask-hello"
        '''
      }
    }
  }
}

