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
                echo "pwd" | sudo -S apt update && sudo -S apt install -y npm
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
