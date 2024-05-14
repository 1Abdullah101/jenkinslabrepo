pipeline {
   
    agent any
  environment{
     DOCKERHUB_CREDENTIALS=credentials('JenkinsLab')           //'JenkinsLab' == Credential ID created in jenkins
  }
    stages{
        stage('Build'){
            steps{
                sh 'npm install'

            }
        }
        stage('test'){
            steps{
                sh 'echo "Test is running"'
            }
        }
        stage('Docker build'){
            steps{
                sh 'docker build -t abdullahtareen/jenkins-integration:latest .'   //'abdullahtareen' == dockerhub username
            }
        }
        stage('login'){
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('push'){
            steps{
                sh 'docker push abdullahtareen/jenkins-integration:latest'          //'abdullahtareen' == dockerhub username
            }
        }
        stage('deploy'){
            steps{
                sh 'echo "Deploying the application"'
            }
        }
      
    }




}