pipeline {
    agent any

    environment {
        APP_PORT = '8000'
    }

    stages {

        stage('Checkout Code') {
            steps {
                git 'https://github.com/mickeyman250-art/Git-pipline-1.git'
            }
        }

        stage('Build') {
            steps {
                echo 'No build needed for static HTML/CSS'
            }
        }

        stage('Run App') {
            steps {
                echo 'Starting simple HTTP server...'
                sh '''
                nohup python3 -m http.server ${APP_PORT} &
                '''
                sleep 5
            }
        }

        stage('Verify App') {
            steps {
                echo 'Checking if app is running...'
                sh 'curl http://localhost:${APP_PORT}'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Static site deployed (served locally)'
            }
        }
    }
}
