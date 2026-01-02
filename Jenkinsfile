pipeline {
    agent any

    tools {
        nodejs 'nodejs'
    }

    stages {

        stage('Clone Repo') {
            steps {
                git branch: 'main', url: 'https://github.com/Dhiraj12-2004/nodejs.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Test') {
            steps {
                sh 'npm test || echo "No tests found"'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                /usr/local/bin/pm2 stop nodejs-app || true
                /usr/local/bin/pm2 start app.js --name nodejs-app
                /usr/local/bin/pm2 save
                '''
            }
        }
    }
}
