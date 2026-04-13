pipeline {
    agent any

    stages {
        stage('Checkout SCM') {
            steps {
                checkout scm
            }
        }
        stage('Setup') {
            steps {
                sh 'pip3 install --break-system-packages --upgrade pip'
                sh 'pip3 install --break-system-packages -r requirements.txt'
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
                archiveArtifacts artifacts: 'model.pkl, metrics.json'
            }
        }
    }
}