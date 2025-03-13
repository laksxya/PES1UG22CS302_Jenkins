pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'g++ -o PES1UG22CS302-1 main/hello.cpp'
                echo 'Build Stage Successful'
            }
        }

        stage('Test') {
            steps {
                sh './PES1UG22CS302-1'
                echo 'Test Stage Successful'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deployment Successful'
            }
        }
    }

    post {
        failure {
            echo 'Pipeline failed'
        }
    }
}
