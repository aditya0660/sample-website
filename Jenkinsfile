pipeline {
    agent any

    environment {
        SERVER_IP = "192.168.1.100"
        USERNAME = "my_username"
        PASSWORD = "my_password"
        WEB_SERVER = "172.30.31.129"
        WEB_USER = 'jenkins'
        WEB_PATH = '/var/www/html'
    }
    stages {
        stage('cloning') {
            steps {
                git branch: 'main', credentialsId: '1', url: 'https://github.com/aditya0660/sample-website.git'
            }
        }
        stage('cleaning') {
            steps {
                sh ' ssh ${WEB_USER}@${WEB_SERVER} '
                sh ' ssh ${WEB_USER}@${WEB_SERVER}:rm -rf ${WEB_PATH}/* ' 
            }
        }
        stage('deploying') {
            steps {
                sh ' sudo scp -r ${WORKSPACE}/* ${WEB_USER}@${WEB_SERVER}:${WEB_PATH}} '
            }
        }
    }
}
