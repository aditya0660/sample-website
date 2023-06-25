pipeline {
    agent any

    environment {
        WEB_USER = 'root'
        WEB_PATH = '/var/www/html/'
    }
    stages {
        stage('cloning') {
            steps {
                git branch: 'main', url: 'https://github.com/aditya0660/sample-website.git'
            }
        }
        stage('deploying') {
            steps {
                sh ' ssh ${WEB_USER}@${WEB_SERVER}:"rm -rf ${WEB_PATH}"'
                sh ' scp -r ${WORKSPACE}/* ${WEB_USER}@${WEB_SERVER}:${WEB_PATH}} '
               //sh ' scp -r /var/lib/jenkins/workspace/pipe/* root@172.30.17.13:/var/www/html/ ' 
            }
        }
    }
}
