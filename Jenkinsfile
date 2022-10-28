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
        docker { image '00cd1fb8bdcc' }
      }
      steps {
        script {
          dir('app') {
            sh '''
              python -m venv env
              env/bin/pip install -r requirements-dev.txt
             
            '''
          }
        }
      }
    }}}