pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                // Pull the latest code from your repository
                git 'https://github.com/Vaishnavi-Peddi/devOps.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                script {
                    // Install dependencies using pip
                    sh 'pip install -r requirements.txt'
                }
            }
        }

        stage('Run Tests') {
            steps {
                // Run unit tests
                sh 'python -m unittest discover tests'
            }
        }

        stage('Build Docker Image') {
            steps {
                // Build a Docker image for the Flask app
                sh 'docker build -t flask-app:latest .'
            }
        }

        stage('Deploy') {
            steps {
                // Run the Docker container
                sh 'docker run -d -p 5000:5000 flask-app:latest'
            }
        }
    }

    post {
        always {
            // Cleanup and notify
            echo 'Pipeline completed'
        }
        success {
            echo 'Pipeline completed successfully'
        }
        failure {
            echo 'Pipeline failed'
        }
    }
}
