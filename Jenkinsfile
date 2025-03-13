pipeline {
agent any
   environment {
        SUDO_PASS = credentials('sudo-password')
    }
    stages {
        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }
  
        stage('Install and Test') {
            steps {
                sh "echo $SUDO_PASS | sudo -S apt install npm"
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
