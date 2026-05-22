pipeline {
    agent any

    tools {
        jdk 'JDK21'
        maven 'Maven3'
    }

    stages {

        stage('GitHub Checkout') {
            steps {
                git 'https://github.com/AyushT05/sample-app.git'
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

        stage('Docker Push') {
            steps {
                bat 'docker push ayusht05/sample-app'
            }
        }
    }
}