pipeline {
    agent none
    stages {
        stage('Checkout') { // Checkout (git clone ...) the projects repository
        agent {
             label 'agent1'
}
      steps {
        checkout scm
      }
    }
        stage('Build') {
           agent {
             label 'agent1'
}
            steps {
                sh 'pip --version'
            }
        }
    }
}