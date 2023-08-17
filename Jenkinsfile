pipeline {
//  agent {
//    dockerContainer {
//      image 'alpine' // Docker-in-Docker image
//      args '-v /var/run/docker.sock:/var/run/docker.sock'
//     }
//   }
   agent any
//   agent { label 'NODE2' }

   options {
        buildDiscarder(
            logRotator(
                numToKeepStr: '1',
                daysToKeepStr: '7',
                artifactDaysToKeepStr: '',
                artifactNumToKeepStr: ''
            ),
            workspaceCleaner(
                cleanWhenSuccess: true,
                cleanWhenUnstable: true,
                cleanWhenFailure: true,
                cleanWhenAborted: true,
                externalDelete: false,
                deleteDirs: true
            )
        )
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
