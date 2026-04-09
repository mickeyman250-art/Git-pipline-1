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
                echo 'Checking files HTML/CSS'
                sh 'ls -lha'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Starting simple HTTP server...'
                sh '''
                sudo rm -rf /var/www/html/*
                sudo cp -r * /var/www/html/  
                nohup python3 -m http.server ${APP_PORT} --bind 0.0.0.0 > server.log 2>&1 &
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
        echo 'Deploying to Nginx root...'
        sh '''
        sudo cp -r /var/lib/jenkins/workspace/Sign-up\ Form /var/www/html/Sign-up-Form/
        sudo systemctl reload nginx
        '''
            }
        }
    }
}