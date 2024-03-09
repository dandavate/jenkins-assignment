pipeline {
    agent any

    stages {
        stage('SCM') {
            steps {
                git branch: 'master', url: 'https://github.com/dandavate/jenkins-assignment.git'
            }
        }


        stage('Preparation') {
            steps {
                script {
                    // Define your Docker image name and container name
                    def dockerImage = 'prod:latest'
                    def containerName = 'production'
                    
                    // Check if the container is running
                    def isContainerRunning = sh(script: "docker ps -q -f name=${containerName}", returnStatus: true) == 0
                    
                    // If the container is running, stop and remove it
                    if (isContainerRunning) {
                        echo "Stopping and removing existing Docker container: ${containerName}"
                        sh "docker stop ${containerName}"
                        sh "docker rm ${containerName}"
                    }
                    
                    // Remove the Docker image if it exists
                    def isImageExists = sh(script: "docker images -q ${dockerImage}", returnStatus: true) == 0
                    if (isImageExists) {
                        echo "Removing existing Docker image: ${dockerImage}"
                        sh "docker rmi ${dockerImage}"
                    }
                }
            }
        }



        
        stage('Docker Build') {
            steps {
                sh 'docker build -t prod:latest .'
            }
        }
      
       stage('Docker Deploy') {
            steps {
                sh 'docker run --name production -d -p 82:80 prod:latest'
            }
        }
        
         stage('Success') {
            steps {
                echo 'Deploy successfull'
            }
        }
        
    }
}
