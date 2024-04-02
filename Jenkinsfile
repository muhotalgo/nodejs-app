pipeline {
    agent any
    stages {
        stage('git scm update') {
            steps {
                git url: 'https://github.com/muhotalgo/nodejs-app.git', branch: 'main'
            }
        }
        stage('docker build & deploy') {
            steps {
        				sh '''
        				docker compose up --build -d
        				'''
            }
        }
    }
}
