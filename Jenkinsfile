pipeline {
    agent any

    environment {
        APP_PORT = '8000'
    }

    stages {

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
                echo "Myname1s@rqam" sudo rm -rf /var/www/html/*
                echo "Myname1s@rqam" sudo cp -r * /var/www/html/  
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
    }
}