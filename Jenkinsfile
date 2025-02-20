pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: 'main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/vastevenson/pytest-intro-vs.git']]])
            }
        }
        stage('Build') {
            steps {
                git branch: 'main', url: 'https://github.com/Siddharth1325/jenkins-python-build-test-demo-vs.git'
                sh 'python3 ops.py'
            }
        }
        stage('Set up Virtual Environment') {
            steps {
                sh 'python3 -m venv venv'
                sh '. venv/bin/activate && pip install pytest'  // For Linux/macOS
                
            }
        }
        stage('Test') {
            steps {
                 sh '. venv/bin/activate && python3 -m pytest' 
            }
        }
    }
}
