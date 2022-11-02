pipeline {
    agent none
    stages {
        stage('Build') {
           agent {
             label 'agent1'
}
            steps {
                sh 'python Hello-World.py'
            }
        }
    }
}