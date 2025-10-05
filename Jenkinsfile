pipeline {
    agent { label 'slave-node' }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
                sh "pwd"
            }
        }

        stage('Install python and pip') {
            steps {
                sh '''
                  sudo apt update
                  sudo apt install python3 -y
                  sudo apt install python-pip3 -y
                '''
            }
        }

        stage('Copy and run File') {
            steps {
                sh '''
                sudo cp app.py /opt/app.py
                nohup python3 app.py
                '''
            }
        }
    }
}
