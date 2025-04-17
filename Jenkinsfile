pipeline {
    agent any
    stages {
        stage('Fetch Code') {
            steps {
                script {
                    git branch: 'main', url: 'https://github.com/SaleemAH75/Jankinsbuild.git'
                }
            }
        }

        stage('Check Python Version') {
            steps {
                script {
                    sh 'python3 --version'
                }
            }
        }

        stage('Create Virtual Environment') {
            steps {
                script {
                    sh 'python3 -m venv venv'
                }
            }
        }

        stage('Install Dependencies') {
            steps {
                script {
                    sh '''
                        . venv/bin/activate
                        pip install --upgrade pip
                        # Commenting out this line if you don’t need any packages
                        # pip install -r requirements.txt
                    '''
                }
            }
        }
    }

    post {
        always {
            cleanWs()
        }
        success {
            echo '✅ Build was successful!'
        }
        failure {
            echo '❌ Build failed!'
        }
    }
}
