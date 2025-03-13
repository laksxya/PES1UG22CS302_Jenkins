pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                // Clone your GitHub repository from the main branch
                git branch: 'main', url: 'https://github.com/laksxya/PES1UG22CS302_Jenkins.git'
            }
        }
        stage('Install Dependencies') {
            steps {
                // Install Node.js dependencies
                sh 'npm install'
            }
        }
        stage('Build Application') {
            steps {
                // Build your application (adjust the command if necessary)
                sh 'npm run build'
            }
        }
        stage('Test Application') {
            steps {
                // Run your tests (adjust the command if necessary)
                sh 'npm test'
            }
        }
        stage('Push Docker Image') {
            steps {
                // Build the Docker image and tag it with the Jenkins build number
                sh 'docker build -t pes1ug22cs302/pes1ug22cs302_pipeline:$BUILD_NUMBER .'
                // Push the Docker image to Docker Hub
                sh 'docker push pes1ug22cs302/pes1ug22cs302_pipeline:$BUILD_NUMBER'
            }
        }
    }
    post {
        failure {
            echo 'Pipeline failed'
        }
    }
}
