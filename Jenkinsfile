pipeline {
    agent any

    environment {
        IMAGE_NAME = "portfolio-app"
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/aryan-bhoi/Portfolio.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh """
                    docker build -t ${IMAGE_NAME} - <<EOF
                    FROM nginx:alpine
                    COPY . /usr/share/nginx/html
                    EXPOSE 80
                    EOF
                    """
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    sh "docker rm -f ${IMAGE_NAME} || true"
                    sh "docker run -d -p 8080:80 --name ${IMAGE_NAME} ${IMAGE_NAME}"
                }
            }
        }
    }

    post {
        always {
            echo "Pipeline finished. Open http://localhost:8080 to view the app."
        }
    }
}