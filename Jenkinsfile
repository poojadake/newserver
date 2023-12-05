pipeline {
    agent any

    environment {
        NODEJS_VERSION = '12' // Change this to the desired Node.js version
        APP_NAME = 'Learning-Ocean'
        AWS_ACCESS_KEY_ID = credentials('c2378e26-9aff-47d9-a856-353293dc68e2')
        AWS_SECRET_ACCESS_KEY = credentials('ce16ff6e-54ee-4bdb-afad-bc7a48ad6089')
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
                    sh "cd ${REPO_PATH} && ${npmCommand}"
                }
            }
        }

        stage('Install Nodemon') {
            steps {
                script {
                    sh 'npm install -g nodemon'
                }
            }
        }

        stage('Start Node Server') {
            steps {
                script {
                    def nodemonCommand = 'nodemon start'
                    sh "cd ${REPO_PATH} && ${nodemonCommand}"
                }
            }
        }
    }

    post {
        always {
            // Clean up: No need to terminate screen session as it's not used
        }
    }
}
