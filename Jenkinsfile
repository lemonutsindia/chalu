pipeline {
    agent any  // Uses any available agent. Change if using a specific agent.

    environment {
        PYTHON_ENV = 'python3'  // Modify if a specific Python version is required
    }

    stages {
        stage('Preparation') {
            steps {
                echo "Starting Jenkins pipeline..."
                sh '''
                    sudo apt-get update && sudo apt-get install -y gcc libffi-dev libssl-dev python3-pip
                '''
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'pip3 install -r requirements.txt'
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
        always {
            echo "Pipeline execution finished."
        }
    }
}
