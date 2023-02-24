pipeline {
    agent any

    stages {
        stage('Checkout SCM') {
            steps {
                checkout([$class: 'GitSCM',
                    branches: [[name: '*/i192011']],
                    userRemoteConfigs: [[url: 'https://github.com/hmzakhalid/ControlNet.git']]])
            }
        }

        stage('Set up Python') {
            tools {
                python '3.8'
            }
            steps {
                sh 'python --version'
            }
        }

        stage('Lint with flake8') {
            steps {
                sh 'pip install flake8'
                sh 'flake8 . --count --select=E9,F63,F7,F82 --show-source --statistics'
            }
        }

        stage('Format with black') {
            steps {
                sh 'pip install black'
                sh 'black .'
            }
        }
    }
}
