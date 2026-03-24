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
        sh 'export PATH=$PATH:/usr/local/bin && docker build -t qr-app .'
    }
}

stage('Run Container') {
    steps {
        sh 'export PATH=$PATH:/usr/local/bin && docker rm -f qr-container || true'
        sh 'export PATH=$PATH:/usr/local/bin && docker run -d -p 3000:3000 --name qr-container qr-app'
    }
}

    }
}