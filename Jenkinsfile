pipeline {
    agent any

    stages {
        stage('Clone GitHub Repo') {
            steps {
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'Github-ssh', url: 'git@github.com:PreciousOdiase/jenkins-scm.git']])
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t dockerfile .'
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    sh 'docker run -itd --name nginx -p 8081:80 dockerfile'
                }
            }
        }
    }
}

