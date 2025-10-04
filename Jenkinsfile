pipeline {
    agent { label 'slave-node' }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install Nginx') {
            steps {
                sh '''
                  sudo apt-get update
                  sudo apt-get install -y nginx
                '''
            }
        }

        stage('Copy HTML File') {
            steps {
                sh '''
                sudo cp index.html /var/www/html/index.html
                '''
            }
        }

        stage('Restart Nginx') {
            steps {
                sh '''
                sudo systemctl restart nginx
                sudo systemctl enable nginx
                '''
            }
        }

        stage('Verify Nginx') {
            steps {
                sh '''
                sudo systemctl status nginx
                curl -I http://localhost
                '''
            }
        }
    }
}
