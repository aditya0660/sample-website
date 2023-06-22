pipeline {
    agent any

    environment{
        web-server-ip = '172.30.31.129'
        web-server-user = 'jenkins'
        web-server-path = '/var/www/html'
    }

    stages {
        stage('cloning') {
            steps {
                git branch: 'main', credentialsId: '1', url: 'https://github.com/aditya0660/sample-website.git'
            }
        }
        stage('Deploying') {
            steps {
                sh 'ssh ${web-server-user}@${web-server-ip}', sh 'sudo rm -rf ${web-server-path}/*' 
                sh 'sudo scp -r ${WORKSPACE}/* ${web-server-user}@${web-server-ip:${web-server-path}}'
            }
        }
    }
}
