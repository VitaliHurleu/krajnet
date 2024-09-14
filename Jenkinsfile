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
            steps {
                sh 'docker-compose up -d'
                echo 'up gitlab ce pause 180 sec'
/*                sh 'sleep 180' */
            }
        }
        stage('Test image') {
            steps {
/*                sh 'docker exec -it gitlab-ce cat /etc/gitlab/ssh_host_ed25519_key.pub' >> ssh_host_key1.pub
                sh 'cat ssh_host_key1.pub' */
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
