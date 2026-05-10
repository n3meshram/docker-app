pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t flask-jenkins-demo .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker rm -f flask-demo || true

                docker run -d \
                  --name flask-demo \
                  -p 5000:5000 \
                  flask-jenkins-demo
                '''
            }
        }

    }
}