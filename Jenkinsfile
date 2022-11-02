pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }
    stage('Test python app') {
      agent agent1
      steps {
        script {
          {
            sh '''
              python -m venv env
              env/bin/pip install -r requirements-dev.txt
             
            '''
          }
        }
      }
    }}}