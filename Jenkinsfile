pipeline {
    agent { label 'slave-node' }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
                sh "pwd"
            }
        }

        stage('Install python flask and pip') {
            steps {
                sh '''
                  sudo apt update
                  sudo apt install python3 -y
                  sudo apt install python3-pip -y
                  sudo python3 -m pip3 install -r requirements.txt
                '''
            }
        }

        stage('Copy and run File') {
            steps {
                sh '''
                    sudo cp app.py /opt/app.py
                    nohup python3 app.py &
                '''
            }
        }
    }
}
