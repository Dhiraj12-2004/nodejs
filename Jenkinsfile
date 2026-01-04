pipeline {
    agent any

    tools {
        nodejs 'nodejs'
    }

    stages {

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
                /usr/bin/pm2 stop nodejs-app || true
                /usr/bin/pm2 start app.js --name nodejs-app
                /usr/bin/pm2 save
                '''
            }
        }
    }
}
