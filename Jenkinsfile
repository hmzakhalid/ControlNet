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

        stage('Lint with flake8') {
            steps {
                sh 'pip install flake8'
                sh '/home/ec2-user/.local/bin/flake8 . --count --select=E9,F63,F7,F82 --show-source --statistics'
            }
        }

        stage('Format with black') {
            steps {
                sh 'pip3 install black'
                sh '/home/ec2-user/.local/bin/black .'
            }
        }
    }
}