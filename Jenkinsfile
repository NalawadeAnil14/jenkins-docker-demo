pipeline {
//  agent {
//    dockerContainer {
//      image 'alpine' // Docker-in-Docker image
//      args '-v /var/run/docker.sock:/var/run/docker.sock'
//     }
//   }

   agent { label 'NODE2' }

   options {
      buildDiscarder(logRotator(numTokeepStr:'1', daysToKeepStr: '7'))
   }

   stages {
    stage('Check user') {
      steps {
        sh 'whoami'
//        sh 'usermod -aG docker devops1' // Add Jenkins user to the Docker group
//        sh 'docker info' // Test Docker command
       }
    }
     
    stage('docker_build'){
      steps {
        sh 'docker build -t python-image .'  
      }
    } 

    stage('docker_run'){
      steps {
        sh 'docker run -itd python-image'
      }
    }
  } 
}
