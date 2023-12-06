pipeline {
    agent any

    environment {
        NODEJS_VERSION = '12' // Change this to the desired Node.js version
        APP_NAME = 'Learning-Ocean'
        AWS_ACCESS_KEY_ID = 'AKIAU2CGDU3WXKM7O5O3'
        AWS_SECRET_ACCESS_KEY = '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'
        REPO_PATH = "/var/lib/jenkins/workspace/nodejs-project/${APP_NAME}"
    }

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/Sachintech-github/Learning-Ocean.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                script {
                    def npmCommand = 'npm install'
                    dir(REPO_PATH) {
                        sh npmCommand
                    }
                }
            }
        }

        stage('Start Node Server') {
            steps {
                script {
                    dir(REPO_PATH) {
                        def nodemonCommand = 'nodemon start'
                        sh nodemonCommand
                    }
                }
            }
        }
    }

    post {
        always {
            // A simple echo statement to ensure there's at least one step in the always block
            echo 'Pipeline completed.'
        }
    }
}
