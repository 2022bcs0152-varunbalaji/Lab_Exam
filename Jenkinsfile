pipeline {
    agent any

    stages {

        stage('Setup') {
            steps {
                sh 'apt-get update && apt-get install -y python3 python3-pip && python3 -m pip install --upgrade pip && python3 -m pip install -r requirements.txt'
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