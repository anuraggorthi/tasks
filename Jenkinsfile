pipeline{
    agent any
    
    environment {
        PATH = "C:\\Program Files\\Docker\\Docker\\resources\\bin;${env.PATH}"
    }

    stages{
        stage("checkout"){
            steps{
                echo "========executing checkout========"
                checkout scm
            }
        }            
        stage("build docker image"){
            steps{
                script{
                  echo "========executing settingup environment========"
                  bat 'docker build -t flask-jenkins-image:latest .'
                }
            }
        }
        
        stage("Deploy Docker Container"){
            steps{
                script{
                    bat 'docker stop flask-container || exit 0'
                    bat 'docker rm flask-container || exit 0'
                    bat 'docker run -d -p 5000:5000 --name flask-container flask-jenkins-image:latest'
                }
            }
        }
    }
}    
    
        