pipeline {
    agent any
    stages {
        stage('fetch') {
            steps {
                script {
                    git branch: 'develop', url: 'https://github.com/dandavate/jenkins-assignment.git'
                }
            }
        }

        stage('build') {

            steps {
                script {
                    docker -t . develop-image
                    }
                }
            }
        }
    }

