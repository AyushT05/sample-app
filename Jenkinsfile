pipeline {
    agent any

    environment {
        DOCKER_TOKEN = 'dckr_pat_OXAUZu73ROdlnuxrek5p8gT2BTg'
    }

    tools {
        jdk 'JDK21'
        maven 'Maven3'
    }

    stages {

        stage('GitHub Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/AyushT05/sample-app.git'
            }
        }

        stage('Maven Build') {
            steps {
                bat 'mvn clean package'
            }
        }

        stage('Docker Build') {
            steps {
                bat 'docker build -t ayusht05/sample-app .'
            }
        }

        stage('Docker Login') {
            steps {
                bat 'docker login -u ayusht05 -p %DOCKER_TOKEN%'
            }
        }

        stage('Docker Push') {
            steps {
                bat 'docker push ayusht05/sample-app'
            }
        }
    }
}