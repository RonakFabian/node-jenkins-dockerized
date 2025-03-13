pipeline {
agent any
  
    stages {
      stage('Init Webhook'){
        steps {
          checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'ca6913cc-ca3d-4778-a7a5-f525ba265635', url: 'https://github.com/RonakFabian/node-jenkins-dockerized.git']])
        }
      }
        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }
  
        stage('Install and Test') {
            steps {
                sh 'sudo apt install npm'
                sh 'npm install -g sonarqube-scanner'
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
               sh 'sudo docker build -t node-image:latest .'
            }
        }
    }
}
