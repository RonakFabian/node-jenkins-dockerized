pipeline {
    agent any

    

    stages {
        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }
    }
   stages {
        stage('Install and Test') {
            steps {
                sh 'sudo apt install npm'
                sh 'npm run test'
            }
        }
    }
   stages {
        stage('Build Npm') {
            steps {
               sh 'npm run build'
            }
        }
    }
  stages {
        stage('Build Docker Image') {
            steps {
               sh 'sudo docker build -t node-image:latest .'
            }
        }
    }
}
