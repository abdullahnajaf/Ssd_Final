pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                echo 'Cloning latest code from GitHub'
                git branch: 'main',
                    url: 'https://github.com/abdullahnajaf/Ssd_Final',
                    credentialsId: 'github-token' // replace with the ID of your GitHub PAT credentials in Jenkins
            }
        }

        stage('Install Dependencies') {
            steps {
                echo 'Installing Python dependencies'
                bat '''
                    python --version
                    pip install --upgrade pip
                    pip install -r requirements.txt
                '''
            }
        }

        stage('Run Unit Tests') {
            steps {
                echo 'Running unit tests'
                bat '''
                    pytest test_app.py
                '''
            }
        }

        stage('Build Application') {
            steps {
                echo 'Building application'
                bat '''
                    if not exist build mkdir build
                    copy app.py build
                '''
            }
        }

        stage('Deploy Application') {
            steps {
                echo 'Deploying application (simulation)'
                bat '''
                    if not exist C:\\deployment mkdir C:\\deployment
                    copy build\\* C:\\deployment
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
