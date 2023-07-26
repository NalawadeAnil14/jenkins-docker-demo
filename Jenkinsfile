pipeline {
  agent any 

   stages {

    stage('Add jenkins use in docker group') {
      steps {
        sh 'usermod -aG docker jenkins' // Add Jenkins user to the Docker group
        sh 'docker info' // Test Docker command
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