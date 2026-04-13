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
                sh '''
                    # Install Python3 without sudo (CI agents often run as root)
                    if ! command -v python3 &> /dev/null; then
                        apt-get update -y && apt-get install -y python3 python3-pip || \
                        apk add --update python3 py3-pip || \
                        echo "Warning: Python installation fallback triggered"
                    fi
                    
                    python3 -m pip install --break-system-packages --upgrade pip
                    python3 -m pip install --break-system-packages -r requirements.txt
                '''
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