pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/ahmadhashir/devops-lab-app.git'
            }
        }
        
        stage('Build Docker Image') {
            steps {
                bat 'docker build -t devops-lab-app .'
            }
        }
        
        stage('Run Container') {
            steps {
                bat 'docker stop myapp || ver>nul'
                bat 'docker rm myapp || ver>nul'
                bat 'docker run -d -p 5000:5000 --name myapp devops-lab-app'
            }
        }
        
        stage('Test') {
            steps {
                bat 'curl http://localhost:5000'
            }
        }
    }
}