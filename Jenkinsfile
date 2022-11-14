pipeline {
    agent none
    stages {
        stage('Checkout') { // Checkout (git clone ...) the projects repository
      steps {
        checkout scm
      }
    }
        stage('Build') {
           agent {
             label 'agent1'
}
            steps {
                sh 'python -m Hello-World.py'
            }
        }
    }
}