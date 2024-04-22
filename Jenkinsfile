pipeline {
    agent { label 'agent' }

    stages {
        stage('git scm update') {
            steps {
                git url: 'https://github.com/muhotalgo/nodejs-app.git', branch: 'main'
            }
        }
        stage('docker build & deploy') {
            steps {
                sh 'IMAGE_NAME=muhotalgo/nodejsapp docker compose build'
            }
        }
    	stage('docker hub push') {
            steps {
                sh '''
 		        docker login -u muhotalgo -p cupleona23$
                docker push muhotalgo/nodejsapp
		        '''
            }
        }
	    stage('microk8s run pod') {
            steps {
                sh ' microk8s kubectl run app1 --image=siestageek/nodejsapp '
            }
        }
    }
}
