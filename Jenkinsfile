pipeline {
    agent any

    environment {
        IMAGE_NAME = 'portfolio-site'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/aryan-bhoi/Portfolio.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("${IMAGE_NAME}:latest")
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    sh '''
                    docker rm -f portfolio-container || true
                    docker run -d --name portfolio-container -p 8081:80 ${IMAGE_NAME}:latest
                    '''
                }
            }
        }
    }

    post {
        always {
            echo "Pipeline finished. Visit http://localhost:8081"
        }
        failure {
            echo "Pipeline failed. Check logs."
        }
    }
}
