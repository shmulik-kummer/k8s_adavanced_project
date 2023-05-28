pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/avielb/rmqp-example'
            }
        }

        stage('Build Docker Image - Producer') {
            steps {
                dir('producer') {
                    // Build the Docker image for the producer
                    sh 'docker build -t kummer/producer .'
                }
            }
        }

        stage('Push Docker Image - Producer') {
            steps {
            script {
                docker.withRegistry('https://index.docker.io/v1/', 'dockerhub')  {
                    // Push the Docker image to Docker Hub
                    sh 'docker push kummer/producer'
                }
            }}
        }

        stage('Build Docker Image - Consumer') {
            steps {
                dir('consumer') {
                    // Build the Docker image for the consumer
                    sh 'docker build -t kummer/consumer .'
                }
            }
        }

        stage('Push Docker Image - Consumer') {
            steps {
            script {
                docker.withRegistry('https://index.docker.io/v1/', 'dockerhub')  {
                    // Push the Docker image to Docker Hub
                    sh 'docker push kummer/consumer'
                }
            }}
        }

        stage('SSH to Kubernetes Server') {
            steps {
                    script {
                    sshagent(credentials: ['k3s']) {
                        sh "ssh vagrant@192.168.56.10"
                        sh "helm version"
                }}
            }
        }

        // Add more stages for subsequent steps as needed
    }
}
