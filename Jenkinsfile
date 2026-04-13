pipeline {
    agent any
    
    stages {
        stage('Checkout SCM') {
            steps {
                checkout scm
            }
        }
        
        stage('Install Python') {
            steps {
                sh '''
                    sudo apt-get update
                    sudo apt-get install -y python3 python3-pip python3-venv
                '''
            }
        }
        
        stage('Setup') {
            steps {
                sh 'python3 -m pip install --user --upgrade pip'
                sh 'python3 -m pip install --user -r requirements.txt'
            }
        }
        
        stage('Train') {
            steps {
                sh 'python3 train.py'
            }
        }
        
        stage('Identity') {
            steps {
                echo 'Student | S Varun Balaji | 2022BCS0152 | MLOps Lab Exam'
            }
        }
        
        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'model.pkl,metrics.json', allowEmptyArchive: true
            }
        }
    }
}