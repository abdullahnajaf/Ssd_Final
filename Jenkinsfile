pipeline {
    agent any
    
    stages {
        stage('Clone Repository') {
            steps {
                echo 'Cloning latest code from GitHub'
                git branch: 'main',
                    url: 'https://github.com/abdullahnajaf/Ssd_Final'
            }
        }
        
        stage('Install Dependencies') {
            steps {
                echo 'Installing Python dependencies'
                sh '''
                    python --version
                    pip install --upgrade pip
                    pip install -r requirements.txt
                '''
            }
        }
        
        stage('Run Unit Tests') {
            steps {
                echo 'Running unit tests'
                sh '''
                    pytest test_app.py
                '''
            }
        }
        
        stage('Build Application') {
            steps {
                echo 'Building application'
                sh '''
                    mkdir -p build
                    cp app.py build/
                '''
            }
        }
        
        stage('Deploy Application') {
            steps {
                echo 'Deploying application (simulation)'
                sh '''
                    mkdir -p /tmp/deployment
                    cp -r build/* /tmp/deployment/
                '''
            }
        }
    }
    
    post {
        success {
            echo 'Pipeline executed successfully!'
        }
        failure {
            echo 'Pipeline failed. Please check logs.'
        }
    }
}

