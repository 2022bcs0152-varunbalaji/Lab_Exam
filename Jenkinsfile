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
                sh 'which python3 || which python || echo "Python not found"'
                sh 'python3 -m pip install --break-system-packages --upgrade pip'
                sh 'python3 -m pip install --break-system-packages -r requirements.txt'
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
                archiveArtifacts artifacts: 'model.pkl, metrics.json'
            }
        }
    }
}