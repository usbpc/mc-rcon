pipeline {
  agent {
    docker {
      image 'gradle:jdk8-alpine'
      args '-m 200m'
    }
    
  }
  stages {
    stage('Inizialize') {
      steps {
        sh '''echo PATH = ${PATH}
echo HOME = ${HOME}
ls /root
gradle clean'''
      }
    }
    stage('Build') {
      steps {
        sh 'gradle jar'
      }
    }
    stage('Archive') {
      parallel {
        stage('Archive') {
          steps {
            archiveArtifacts 'build/libs/*'
          }
        }
        stage('Print home') {
          steps {
            sh '''ls /root
ls /root/.gradle'''
          }
        }
      }
    }
  }
}