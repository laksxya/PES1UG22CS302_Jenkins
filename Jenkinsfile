pipeline {
    agent {
        docker {
            image 'node:16'
        }
    }

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/laksxya/PES1UG22CS302_Jenkins.git'
            }
        }
        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }
        stage('Build Application') {
            steps {
                sh 'npm run build'
            }
        }
        stage('Test Application') {
            steps {
                sh 'npm test'
            }
        }
    }
    post {
        failure {
            echo 'Pipeline failed'
        }
    }
}
