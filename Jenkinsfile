pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git 'https://github.com/YOUR_USERNAME/ci-cd-ngrok-app.git'
            }
        }
        stage('Install Dependencies') {
            steps {
                sh 'pip install -r requirements.txt'
            }
        }
        stage('Run Tests') {
            steps {
                sh 'pytest test_app.py'
            }
        }
        stage('Start Flask App') {
            steps {
                sh 'nohup python app.py &'
                sleep(time: 5, unit: 'SECONDS')
            }
        }
        stage('Start Ngrok') {
            steps {
                sh './start_ngrok.sh'
            }
        }
    }
}
