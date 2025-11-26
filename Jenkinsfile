pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/coderritesh/static-website.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh '''
                docker build -t static-website:latest .
                '''
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker rm -f static-website-container || true
                docker run -d --name static-website-container -p 8081:80 static-website:latest
                '''
            }
        }
    }
}
