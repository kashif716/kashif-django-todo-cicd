pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'develop', url: 'https://github.com/kashif716/kashif-django-todo-cicd.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t django-todo:latest .'
            }
        }
        stage('Run Container') {
            steps {
                sh 'docker stop todo-app || true'
                sh 'docker rm todo-app || true'
                sh 'docker run -d -p 8000:8000 --name todo-app django-todo:latest'
            }
        }
    }
}