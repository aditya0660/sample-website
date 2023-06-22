pipeline {
    agent any

    environment {
        WEB-SERVER = 172.30.31.129
        WEB-USER = 'jenkins'
        WEB-PATH = '/var/www/html'
    }

    stages {
        stage('cloning') {
            steps {
                git branch: 'main', credentialsId: '1', url: 'https://github.com/aditya0660/sample-website.git'
            }
        }
        stage('Deploying') {
            steps {
                sh 'ssh ${WEB-USER}@${WEB-SERVER}', sh 'sudo rm -rf ${WEB-PATH}/*' 
                sh 'sudo scp -r ${WORKSPACE}/* ${WEB-USER}@${WEB-SERVER}:${WEB-PATH}}'
            }
        }
    }
}
