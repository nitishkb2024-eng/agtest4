pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Show Build Info') {
            steps {
                // Windows batch uses %variable% styling in echo commands, 
                // but Jenkins environment string interpolation remains the same
                echo "BUILD_NUMBER: ${env.BUILD_NUMBER}"
                echo "JOB_NAME: ${env.JOB_NAME}"
                echo "WORKSPACE: ${env.WORKSPACE}"
            }
        }
        
        stage('Run Linter') {
            steps {
                // Use bat (Batch) instead of sh (Shell)
                bat 'pip install flake8'
                bat 'flake8 app.py'
            }
        }
    }
}
