pipeline {
    agent {
        docker {
            image 'python:3.11-slim'
            args '-v /var/jenkins_home/workspace:/workspace'
        }
    }
    
    stages {
        stage('Checkout SCM') {
            steps {
                checkout scm
            }
        }
        
        stage('Setup') {
            steps {
                sh 'pip install --upgrade pip'
                sh 'pip install -r requirements.txt'
            }
        }
        
        stage('Train') {
            steps {
                sh 'python train.py'
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