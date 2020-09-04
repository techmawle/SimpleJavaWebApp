pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'mvn clean package'
      }
    }

    stage('CopyArtifacts') {
      steps {
        archiveArtifacts 'target/**/*.war'
      }
    }

  }
}