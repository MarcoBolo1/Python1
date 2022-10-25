pipeline {
   agent { docker { image 'python' } }
    // {
    //     node {label 'python'}
    // }
    environment {
        APPLICATION_NAME = 'Hello-World.py'
        GIT_REPO="https://github.com/MarcoBolo1/Python1.git"
        GIT_BRANCH="main"
        STAGE_TAG = "promoteToQA"
        DEV_PROJECT = "dev"
        STAGE_PROJECT = "stage"
        TEMPLATE_NAME = "python-nginx"
        ARTIFACT_FOLDER = "target"
        PORT = 8081;
    }
    stages {
        stage('Get Latest Code') {
            steps {
                git branch: "${GIT_BRANCH}", url: "${GIT_REPO}"
            }
        }
        stage ("Install Dependencies") {
            steps {
                sh """
                pip install virtualenv
                virtualenv --no-site-packages .
                source bin/activate
                pip install -r app/requirements.pip
                deactivate
                """
            }
        }
        stage('Run Tests') {
            steps {
                sh '''
                source bin/activate
                nosetests app --with-xunit
                deactivate
                '''
                junit "nosetests.xml"
            }
        }
        stage('Store Artifact'){
            steps{
                script{
                    def safeBuildName  = "${APPLICATION_NAME}_${BUILD_NUMBER}",
                        artifactFolder = "${ARTIFACT_FOLDER}",
                        fullFileName   = "${safeBuildName}.tar.gz",
                        applicationZip = "${artifactFolder}/${fullFileName}"
                        applicationDir = ["app",
                                            "config",
                                            "Dockerfile",
                                            ].join(" ");
                    def needTargetPath = !fileExists("${artifactFolder}")
                    if (needTargetPath) {
                        sh "mkdir ${artifactFolder}"
                    }
                    sh "tar -czvf ${applicationZip} ${applicationDir}"
                    archiveArtifacts artifacts: "${applicationZip}", excludes: null, onlyIfSuccessful: true
                }
            }
        }
    }
}