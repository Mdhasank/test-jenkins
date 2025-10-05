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
                  sudo python3 -m pip install --break-system-packages -r requirements.txt

                '''
            }
        }

        stage('Copy and run File') {
            steps {
                sh '''
            cp /home/ubuntu/jenkins2/workspace/install-python/app.py /home/ubuntu/my-flask/app.py
            cp /home/ubuntu/jenkins2/workspace/install-python/requirements.txt /home/ubuntu/my-flask/requirements.txt
            cd /home/ubuntu/my-flask/
            sudo python3 -m pip install --break-system-packages -r requirements.txt
            nohup python3 app.py > flask.log 2>&1 &
                '''
            }
        }
    }
}
