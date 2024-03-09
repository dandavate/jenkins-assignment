pipeline {
    agent any

    stages {
        stage('SCM') {
            steps {
                git branch: 'develop', url: 'https://github.com/dandavate/jenkins-assignment.git'
            }
        }
        
        stage('Docker Build') {
            steps {
                sh 'docker build -t . sample-image'
            }
        }
        
         stage('Final') {
            steps {
                echo 'Docker build successfull'
            }
        }
        
    }
}



