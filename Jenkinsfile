pipeline {
    agent any

    environment {
        WEB_SERVER = "172.30.17.13"
        WEB_USER = 'jenkins'
        WEB_PATH = '/var/www/html'
    }
    stages {
        stage('cloning') {
            steps {
                git branch: 'main', url: 'https://github.com/aditya0660/sample-website.git'
            }
        }
        stage('deploying') {
            steps {
                sh ' sudo scp -r ${WORKSPACE}/* ${WEB_USER}@${WEB_SERVER}:${WEB_PATH}} '
            }
        }
    }
}
