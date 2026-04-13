pipeline {
    agent {
        docker { image 'python:3.11-slim' }
    }
    stages {
        stage('Checkout SCM') {
            steps {
                checkout scm
            }
        }
        stage('Setup') {
            steps {
                sh 'python3 -m pip install --upgrade pip'
                sh 'python3 -m pip install -r requirements.txt'
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
                archiveArtifacts artifacts: 'model.pkl,metrics.json'
            }
        }
    }
}