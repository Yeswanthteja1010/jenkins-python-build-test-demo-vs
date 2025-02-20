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
        stage('Test') {
            steps {
                sh 'pip install pytest'  // Add this line to install pytest
                sh 'python3 -m pytest'
            }
        }
    }
}
