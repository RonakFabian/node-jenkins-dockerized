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
                sh 'sudo npm install -g sonarqube-scanner'
                sh 'npm test'
            }
        }

        stage('Build Npm') {
            steps {
               sh 'npm run build'
            }
        }
    
 
  stage('SonarQube Analysis') {
    steps{
    def scannerHome = tool 'sonar';
    withSonarQubeEnv() {
      sh "${scannerHome}/bin/sonar-scanner"
    }
    }
  }

 
        stage('Build Docker Image') {
            steps {
               sh 'sudo docker build -t node-image:latest .'
            }
        }
    }
}
