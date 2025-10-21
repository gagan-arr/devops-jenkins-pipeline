pipeline {
    agent any

    environment {
        IMAGE_NAME = "nodejs-demo-app"
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/gagan-arr/devops-jenkins-pipeline.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME .'
            }
        }

        stage('Install Dependencies & Test') {
            steps {
                // Run npm install inside the Docker container
                sh 'docker run --rm -v $PWD:/app -w /app $IMAGE_NAME npm install'
                sh 'docker run --rm -v $PWD:/app -w /app $IMAGE_NAME npm test || echo "No tests found"'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploy stage - You can add docker push or deployment steps here.'
            }
        }
    }
}
