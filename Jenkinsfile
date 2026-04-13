pipeline {
    agent any

    stages {

        stage('Setup') {
            steps {
                sh '''
                apt update
                apt install -y python3-pip
                pip3 install -r requirements.txt
                '''
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