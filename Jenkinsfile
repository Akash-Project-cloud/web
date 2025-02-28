pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/Akash-Project-cloud/web.git'
            }
        }
        stage('Deploy to EC2') {
            steps {
                sh 'scp -i devops-key.pem -o StrictHostKeyChecking=no -r * ubuntu@65.2.183.155:/var/www/html/'
            }
        }
        stage('Restart Web Server') {
            steps {
                sh 'ssh -i devops-key.pem ubuntu@65.2.183.155 "sudo systemctl restart apache2"'
            }
        }
    }
}
