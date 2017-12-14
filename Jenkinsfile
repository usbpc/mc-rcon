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
        sh '''pwd
if [ -d "/root" ]; then
    ls -a /root
fi
if [ -d "/root/.gradle" ]; then
    touch /root/.gradle/testFile
    ls -a /root/.gradle
fi
if [ -d "/root/.gradle" ]; then
    ls -a /root/.gradle
fi
if [ -d "/root/.gradle/caches" ]; then
    ls -a /root/.gradle/caches
fi
if [ -d "/root/.gradle/caches/jars-3" ]; then
    ls -a /root/.gradle/caches/jars-3
fi
gradle clean
if [ -d "/root" ]; then
    ls -a /root
fi
if [ -d "/root/.gradle" ]; then
    ls -a /root/.gradle
fi
if [ -d "/root/.gradle" ]; then
    ls -a /root/.gradle
fi
if [ -d "/root/.gradle/caches" ]; then
    ls -a /root/.gradle/caches
fi
if [ -d "/root/.gradle/caches/jars-3" ]; then
    ls -a /root/.gradle/caches/jars-3
fi'''
      }
    }
    stage('Build') {
      steps {
        sh '''pwd
gradle jar'''
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
            sh '''pwd
if [ -d "/root" ]; then
    ls -a /root
fi
if [ -d "/root/.gradle" ]; then
    ls -a /root/.gradle
fi
if [ -d "/root/.gradle" ]; then
    ls -a /root/.gradle
fi
if [ -d "/root/.gradle/caches" ]; then
    ls -a /root/.gradle/caches
fi
if [ -d "/root/.gradle/caches/jars-3" ]; then
    ls -a /root/.gradle/caches/jars-3
fi'''
          }
        }
      }
    }
  }
}