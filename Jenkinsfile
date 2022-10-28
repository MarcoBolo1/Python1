pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }
    stage('Test python app') {
      agent {
        docker { image 'python:3.8.8-slim-buster' }
      }
      steps {
        script {
          dir('app') {
            sh '''
              python -m venv env
              env/bin/pip install -r requirements-dev.txt
              env/bin/pytest . --junit-xml=pytest_junit.xml
            '''
          }
        }
      }
      post {
        always {
          junit testResults: '**/*pytest_junit.xml'