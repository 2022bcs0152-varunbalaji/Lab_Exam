pipeline {
    agent {
        docker {
            image 'python:3.10'
        }
    }
    stages {
        stage('Setup') {
            steps {
                sh 'pip install --upgrade pip'
                sh 'pip install --break-system-packages -r requirements.txt'
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