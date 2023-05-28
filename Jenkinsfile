pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/avielb/rmqp-example'
            }
        }

        stage('Build Producer Docker Image') {
            steps {
                dir('producer') {
                    // Build the Docker image
                    sh 'docker build -t producer .'
                }
            }
        }

        // Add more stages for subsequent steps as needed
    }
}







