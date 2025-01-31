pipeline {
    agent any  // Runs on any available Jenkins agent

    environment {
        PYTHON_PATH = 'C:\\Python39\\python.exe'  // Change this if using a different Python version
    }

    stages {
        stage('Preparation') {
            steps {
                echo "Starting Jenkins pipeline on Windows..."
                bat '''
                    echo Checking installed programs...
                    where gcc
                    where python
                '''
            }
        }

        stage('Install Dependencies') {
            steps {
                bat '''
                    echo Installing Python and GCC if not installed...
                    choco install mingw -y
                    choco install python -y
                    set PATH=%PATH%;C:\\Program Files\\mingw-w64\\mingw64\\bin
                '''
                bat '%PYTHON_PATH% -m pip install --upgrade pip'
                bat '%PYTHON_PATH% -m pip install telebot pymongo aiohttp'
            }
        }

        stage('Compile C Program') {
            steps {
                bat 'gcc bgmi.c -o bgmi -pthread'
            }
        }

        stage('Run Python Script') {
            steps {
                bat '%PYTHON_PATH% vector.py'
            }
        }

        stage('Completion') {
            steps {
                echo "Pipeline completed successfully on Windows!"
            }
        }
    }

    post {
        success {
            echo "Build was successful!"
        }
        failure {
            echo "Build failed. Check logs for details."
        }
    }
}
