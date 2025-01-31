pipeline {
    agent any  // Use any available agent (change if using a specific agent)
    
    environment {
        PYTHON_ENV = 'python3'  // Adjust based on the system
    }
    
    stages {
        stage('Preparation') {
            steps {
                echo "Starting pipeline..."
                sh 'sudo apt-get update && sudo apt-get install -y gcc libffi-dev libssl-dev python3-pip'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'pip3 install telebot pymongo aiohttp'
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

        stage('Completion') {
            steps {
                echo "Pipeline completed successfully!"
            }
        }
    }
    
    post {
        success {
            echo "Build was successful!"
        }
        failure {
            echo "Build failed. Please check logs."
        }
    }
}
