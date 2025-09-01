pipeline {
    agent any

    environment {
        IMAGE_NAME = "portfolio-app"
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/aryan-bhoi/Portfolio.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                echo "Built Docker Image"
            }
        }

        stage('Run Docker Container') {
            steps {
                echo "Docker container running"
            }
        }
    }

    post {
        always {
            echo "Pipeline finished. Open http://localhost:8080 to view the app."
        }
    }
}
