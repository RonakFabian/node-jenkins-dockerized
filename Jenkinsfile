pipeline {
agent any
  
    stages {
        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }
  
        stage('Install and Test') {
            steps {
                sh 'sudo apt install npm'
                sh 'npm test'
            }
        }

        stage('Build Npm') {
            steps {
               sh 'npm run build'
            }
        }
 
        stage('Build Docker Image') {
            steps {
               sh 'docker build -t node-image:latest .'
            }
        }
    }
}
