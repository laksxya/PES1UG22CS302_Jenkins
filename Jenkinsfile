pipeline {
    agent {
        docker {
            // Use an official Maven image that includes JDK and Maven
            image 'maven:3.8.4-jdk-11'
            // Optionally, add args if needed (e.g., to mount the Docker socket if you need Docker commands)
            // args '-v /var/run/docker.sock:/var/run/docker.sock'
        }
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean install'
                echo 'Build Stage Successful'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
                echo 'Test Stage Successful'
            }
            post {
                always {
                    // Archive test results
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage('Deploy') {
            steps {
                sh 'mvn deploy'
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
