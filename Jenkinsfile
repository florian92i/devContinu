pipeline {
  environment {
    registry = "9123456789/integrationcontinu"
    registryCredential = 'eemi-devops-hubdocker'
  }
  agent any
  tools {nodejs "nodejs" }
  stages {
    stage('Cloning Git') {
      steps {
        eemi-devops-github 'https://github.com/Akasam/jenkins-demo1'
        }
    }
    stage('Build') {
       steps {
         sh 'npm install'
       }
    }
    stage('Test') {
      steps {
        sh 'npm test'
      }
    }
    stage('Building image') {
      steps{
        script {
          dockerImage = docker.build registry + ":projet"
        }
      }
    }
    stage('Deploy Image') {
      steps{
        script {
          docker.withRegistry( '', registryCredential ) {
            dockerImage.push()
          }
        }
      }
    }
    stage('Deploy On serveur') {
           steps {
              sh "ssh -o 'StrictHostKeyChecking no' floriancompiegne@35.205.96.241 'docker pull 9123456789/integrationcontinu:projet'"
           }
     }
  }
}


