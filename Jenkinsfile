pipeline{
    agent any
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
                  bat 'docker build -t flask-jenkins-angular-image:latest .'
                }
            }
        }
        
        stage("Deploy Docker Container"){
            steps{
                script{
                bat 'docker rm -f angular-container'    
                bat 'docker run -d -p 5001:5000 --name angular-container flask-jenkins-angular-image:latest'
                }
            }
        }
    }
}    