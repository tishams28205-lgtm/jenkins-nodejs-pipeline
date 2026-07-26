pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'npm install'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t jenkins-nodejs-pipeline .'
            }
        }

        stage('Remove Old Container') {
            steps {
                bat 'docker rm -f jenkins-demo || ver > nul'
            }
        }

        stage('Deploy') {
            steps {
                bat 'docker run -d -p 3002:3000 --name jenkins-demo jenkins-nodejs-pipeline'
            }
        }
    }
}