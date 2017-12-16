pipeline {
  agent {
    docker {
      image 'gradle:jdk8-alpine'
      args '-v gradle_cache:/root/.gradle -m 200m '
    }
    
  }
  stages {
    stage('Inizialize') {
      steps {
        sh '''gradle clean'''
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
        stage('Publish') {
          environment {
            BINTRAY_ACCESS = credentials('bintray-usbpc')
          }
          steps {
            sh 'gradle publish'
          }
        }
      }
    }
  }
}
