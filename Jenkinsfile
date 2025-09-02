pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Clean checkout to avoid old repo issues
                deleteDir()
                git branch: 'main', url: 'https://github.com/aryan-bhoi/Portfolio.git'
            }
        }

        stage('Build') {
            steps {
                echo "Simulate build process..."
            }
        }

        stage('Deploy') {
            steps {
                echo "Simulate deployment process..."
            }
        }
    }

    post {
        always {
            echo "Pipeline finished. Open http://localhost:8080 to view the app."
        }
    }
}