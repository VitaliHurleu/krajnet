pipeline {
    agent {
        label 'Master'
    }
    environment {
        DOCKERHUB_TOKEN = credentials('dockerhub_token')
        imagename = "barabanuser02/testacademy"
        containername = "my-container"
    }
    stages{
        stage('Checkout'){
            steps{
                git url: 'https://github.com/VitaliHurleu/krajnet.git', branch: 'main'
            }
        }
        stage ("Quality Gate") {
            steps {
                echo 'Quality Gate'
            }            
        }    
        stage('Build'){
            steps{
/*                sh 'docker build . -t "${imagename}:latest"' */
                sh 'docker-compose up -d'
                echo 'up gitlab ce'
            }
        }
        stage('Test image') {
            steps {
                echo 'test image'
            }  
        }     
        stage('Push'){
            steps{
                echo 'push image'
            }
        }  
        stage('Deploy'){
            steps{
                echo 'Deploy'
            }
        }               
    }
}
