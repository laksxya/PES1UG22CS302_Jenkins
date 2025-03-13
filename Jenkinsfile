pipeline {
    agent any
    stages {
        stage('Clone repository') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/laksxya/PES1UG22CS302_Jenkins.git'
            }
        }
        stage('Install dependencies') {
            steps {
                sh 'npm install'
            }
        }
        stage('Build application') {
            steps {
                sh 'npm run build'
            }
        }
        stage('Test application') {
            steps {
                sh 'npm test'
            }
        }
        stage('Push Docker image') {
            steps {
                sh 'docker build -t pes1ug22cs302/pes1ug22cs302_pipeline:$BUILD_NUMBER .'
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
