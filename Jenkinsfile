pipeline {
   
    agent any
  environment{
     DOCKERHUB_CREDENTIALS=credentials('JenkinsLab')           //'JenkinsLab' == Credential ID created in jenkins
  }
    stages{
        stage('Build'){
            steps{
                bat 'npm install'

            }
        }
        stage('test'){
            steps{
                bat 'echo "Test is running"'
            }
        }
        stage('Docker build'){
            steps{
                bat 'docker build -t abdullahtareen/jenkins-integration:latest .'   //'abdullahtareen' == dockerhub username
            }
        }
        stage('login'){
            steps{
                bat 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('push'){
            steps{
                bat 'docker push abdullahtareen/jenkins-integration:latest'          //'abdullahtareen' == dockerhub username
            }
        }
        stage('deploy'){
            steps{
                bat 'echo "Deploying the application"'
            }
        }
      
    }




}