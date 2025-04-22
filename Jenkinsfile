pipeline {
    agent any
    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', credentialsId: 'github-credentials', url: 'https://github.com/minnu1102/blossom-flowers.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t blossom-flowers .'
                }
            }
        }
        stage('Run Container') {
            steps {
                script {
                    sh 'docker stop blossom || echo "No container to stop"'
                    sh 'docker rm blossom || echo "No container to remove"'
                    sh 'docker run -d -p 80:80 --name blossom blossom-flowers || echo "Failed to start the container"'
                }
            }
        }
    }
}
