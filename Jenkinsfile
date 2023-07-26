pipeline {
  agent any 

   stages {
    stage('Install docker'){
      steps {
        sh 'sudo apt install docker -y'
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
