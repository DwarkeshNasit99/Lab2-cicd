pipeline {
    agent any
    
    environment {
        PYTHON_VERSION = '3.8'
    }
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Setup Python') {
            steps {
                sh '''
                    python3 -m venv venv
                    . venv/bin/activate
                    pip install -r requirements.txt
                '''
            }
        }
        
        stage('Build') {
            steps {
                sh '''
                    . venv/bin/activate
                    echo "Building application..."
                    python -m compileall .
                '''
            }
        }
        
        stage('Test') {
            steps {
                sh '''
                    . venv/bin/activate
                    python -m pytest test_app.py -v
                '''
            }
        }
        
        stage('Deploy') {
            steps {
                echo "Deployment stage - This would deploy to your cloud provider"
            }
        }
    }
    
    post {
        always {
            emailext (
                subject: "Pipeline ${currentBuild.result}: Job '${env.JOB_NAME}'",
                body: "Check console output at ${env.BUILD_URL}",
                recipientProviders: [[$class: 'DevelopersRecipientProvider']]
            )
        }
    }
} 