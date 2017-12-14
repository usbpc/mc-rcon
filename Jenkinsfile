pipeline {
  agent {
    docker {
      image 'gradle:jdk8-alpine'
      args '-m 200m -v gradle_cache:~/.gradle'
    }
    
  }
  stages {
    stage('Inizialize') {
      steps {
        sh '''echo PATH = ${PATH}
gradle clean'''
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