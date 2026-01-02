stage('Deploy') {
    steps {
        sh '''
        /usr/local/bin/pm2 stop nodejs-app || true
        /usr/local/bin/pm2 start app.js --name nodejs-app
        /usr/local/bin/pm2 save
        '''
    }
}
