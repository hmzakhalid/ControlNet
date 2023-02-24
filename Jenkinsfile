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
                sh '/usr/local/bin/pip install flake8'
                sh '/usr/local/bin/flake8 . --count --select=E9,F63,F7,F82 --show-source --statistics'
            }
        }

        stage('Format with black') {
            steps {
                sh '/usr/local/bin/pip install black'
                sh '/usr/local/bin/black .'
            }
        }
    }
}




