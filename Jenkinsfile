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
        sh 'gradle clean'
      }
    }
    stage('Build') {
      steps {
        sh 'gradle jar'
      }
    }
    stage('Archive') {
      steps {
        archiveArtifacts 'build/libs/*'
      }
    }
  }
}