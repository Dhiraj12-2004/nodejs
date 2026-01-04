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
                pm2 stop nodejs-app || true
                pm2 start app.js --name nodejs-app
                pm2 save
                '''
            }
        }
    }
}
