pipeline {
  agent {
    docker {
      image 'gradle:jdk8-alpine'
      args '-m 200m -v gradle_cache:/root/.gradle'
    }
    
  }
  stages {
    stage('Inizialize') {
      steps {
        sh '''ls -a /root
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
            sh '''ls -a /root
ls /root/.gradle/caches/jars-3'''
          }
        }
      }
    }
  }
}