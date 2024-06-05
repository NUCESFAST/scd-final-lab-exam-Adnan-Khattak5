pipeline {
    agent any

    environment {
        DOCKERHUB_CREDENTIALS = 'dockerhub-credentials'
        DOCKERHUB_USERNAME = 'adnankhattak'
        REPO_NAME = 'scd-final-lab-exam-Adnan-Khattak5'
    }

    stages {
        stage('Checkout Code 1141') {
            steps {
                git 'https://github.com/NUCESFAST/scd-final-lab-exam-Adnan-Khattak5.git'
            }
        }
        
        stage('Install Dependencies 1141') {
            agent {
                docker {
                    image 'node:17' // Use a Node.js Docker image
                    args '-v /var/run/docker.sock:/var/run/docker.sock' // Allow Docker inside Docker
                }
            }
            steps {
                script {
                    def services = ['Auth', 'Classrooms', 'event-bus', 'Post', 'client']
                    for (service in services) {
                        dir(service) {
                            sh 'npm install'
                        }
                    }
                }
            }
        }

        stage('Build Docker Images 1141') {
            steps {
                script {
                    def services = ['Auth', 'Classrooms', 'event-bus', 'Post', 'client']
                    for (service in services) {
                        dir(service) {
                            sh "docker build -t ${DOCKERHUB_USERNAME}/${service.toLowerCase()}:latest ."
                        }
                    }
                }
            }
        }

        stage('Push Images to Docker Hub 1141') {
            steps {
                script {
                    def services = ['Auth', 'Classrooms', 'event-bus', 'Post', 'client']
                    docker.withRegistry('', DOCKERHUB_CREDENTIALS) {
                        for (service in services) {
                            sh "docker push ${DOCKERHUB_USERNAME}/${service.toLowerCase()}:latest"
                        }
                    }
                }
            }
        }

        stage('Deploy and Test 1141') {
            steps {
                script {
                    sh 'docker-compose up -d'
                }
            }
        }
    }
}
