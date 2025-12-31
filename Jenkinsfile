pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }

    stage('Build Image') {
      steps {
        sh 'docker build -t flask-hello:latest .'
      }
    }

    stage('Deploy') {
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
