pipeline {
    agent any

    stages {
        stage('SCM') {
            steps {
                git branch: 'master', url: 'https://github.com/dandavate/jenkins-assignment.git'
            }
        }
        
        stage('Docker Build') {
            steps {
                sh 'docker build -t prod:latest .'
            }
        }
      
       stage('Docker Deploy') {
            steps {
                sh 'docker run -d -p 82:80 prod:latest'
            }
        }
        
         stage('Success') {
            steps {
                echo 'Deploy successfull'
            }
        }
        
    }
}
