pipeline {
    agent any

    stages {

        stage('Setup') {
            steps {
                sh 'echo "Setup stage skipped (no root access)"'
            }
        }

        stage('Train') {
            steps {
                sh 'python3 -m pip install --user pandas numpy scikit-learn joblib'
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