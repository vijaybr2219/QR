pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                git branch: 'main', url: 'https://github.com/vijaybr2219/QR.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                   sh '/usr/local/bin/docker build -t qr-app .'
                }
            }
        }

        stage('Run Container') {
            steps {
                script {
                    sh 'docker rm -f qr-container || true'
                    sh 'docker run -d -p 3000:3000 --name qr-container qr-app'
                }
            }
        }

    }
}