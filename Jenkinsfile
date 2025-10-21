pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/gagan-arr/devops-jenkins-pipeline.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t nodejs-demo-app .'
            }
        }

        stage('Install Dependencies & Test') {
            steps {
                sh 'npm install'
                sh 'npm test'
            }
        }

        stage('Deploy') {
            steps {
                sh 'docker run -d -p 3000:3000 nodejs-demo-app'
            }
        }
    }
}
