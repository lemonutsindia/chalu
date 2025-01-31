pipeline {
    agent any

    environment {
        TELEBOT_API_KEY = credentials('8052073236:AAHXLFvJtenFtrDarJxAzog1puFCDhN7aLQ')  // Store API key securely in Jenkins credentials
    }

    stages {
        stage('Initialize') {
            steps {
                echo "Starting Jenkins pipeline..."
                sh 'sudo apt-get update && sudo apt-get install -y gcc libffi-dev libssl-dev python3-pip'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'pip install telebot pymongo aiohttp'
            }
        }

        stage('Compile C Program') {
            steps {
                sh 'gcc bgmi.c -o bgmi -pthread'
            }
        }

        stage('Run Python Script') {
            steps {
                sh 'python3 vector.py'
            }
        }
    }

    post {
        success {
            echo "Pipeline execution completed successfully!"
        }
        failure {
            echo "Pipeline failed!"
        }
    }
}
