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

////////////////////////////////////////////////////////////////

// pipeline {
//   agent any

//   environment {
//     DOCKERHUB_CREDENTIALS_ID = 'JenkinsLab' // Reference credential ID directly
//   }

//   stages {
//     stage('Checkout Code') { // Improved stage name
//       steps {
//         git branch: 'main', // Assuming your code is in the main branch
//           credentialsId: 'your-git-credentials-id', // Replace with your git credentials ID
//           url: 'https://github.com/your-username/your-repo.git' // Replace with your repository URL
//       }
//     }

//     stage('Build') {
//       steps {
//         bat 'npm install' // Use 'sh' for shell commands (better practice)
//       }
//     }

//     stage('Test') {
//       steps {
//         bat 'echo "Test is running"'
//       }
//     }

//     stage('Docker Build') {
//       steps {
//         script { // Use 'script' for multi-line commands and environment variables
//           docker.build image: 'abdullahtareen/jenkins-integration:latest'
//         }
//       }
//     }

//     stage('Login') {
//       steps {
//         script {
//           def credentials = credentials(id: DOCKERHUB_CREDENTIALS_ID)
//           docker.withRegistry('https://hub.docker.com', credentialsId: credentials.id) {
//             echo 'Logged in to Docker Hub'
//           }
//         }
//       }
//     }

//     stage('Push') {
//       steps {
//         script {
//           docker.push('abdullahtareen/jenkins-integration:latest')
//         }
//       }
//     }

//     stage('Deploy') { // Consider adding a deploy script or specifying deployment method
//       steps {
//         // Replace with your actual deployment commands or script call
//         bat 'echo "Deployment in process"'
//       }
//     }
//   }
// }
