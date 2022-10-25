pipeline {
    agent any
stages {
  stage('Build') {
    steps {
      sh checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/MarcoBolo1/Python1.git']]])
    }
  }

  stage('Tests') {
    steps {
      // One or more steps need to be included within the steps block.
    }
  }

  stage('Deploy') {
    steps {
      // One or more steps need to be included within the steps block.
    }
  }

  stage('Raport') {
    steps {
      // One or more steps need to be included within the steps block.
    }
  }

}
