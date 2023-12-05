pipeline {
    agent any

    environment {
        NODEJS_VERSION = '14' // Change this to the desired Node.js version
        APP_NAME = 'Learning-Ocean'
        AWS_ACCESS_KEY_ID = credentials('c2378e26-9aff-47d9-a856-353293dc68e2')
        AWS_SECRET_ACCESS_KEY = credentials('ce16ff6e-54ee-4bdb-afad-bc7a48ad6089')
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
                    sh "cd ${APP_NAME} && ${npmCommand}"
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
                    def screenSession = 'nodejs-app'
                    def nodemonCommand = 'nodemon start'
                    sh "screen -dmS ${screenSession} bash -c 'cd ${APP_NAME} && ${nodemonCommand}'"
                }
            }
        }
    }

    post {
        always {
            // Clean up: Terminate the screen session when the build is done
            script {
                sh 'screen -XS nodejs-app quit'
            }
        }
    }
}
