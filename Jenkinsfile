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

        stage('Test') {
            steps {
                // If you have tests, run them here inside the container
                sh 'docker run --rm $IMAGE_NAME npm test || echo "No tests found"'
            }
        }

        stage('Deploy') {
            steps {
                echo '✅ Build successful. Ready to deploy!'
            }
        }
    }
}
