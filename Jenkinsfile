pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git branch: 'main',
                    url: git url: 'git@github.com:sufiyaannn84/Node.file.git', branch: 'main'

            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t nodefile-app .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker rm -f nodefile-container || true'
            }
        }

        stage('Run New Container') {
            steps {
                sh 'docker run -d -p 3000:3000 --name nodefile-container nodefile-app'
            }
        }
    }
}
