pipeline {
  agent any
  stages {
    stage('Build') {
      post {
        success {
          archiveArtifacts(artifacts: 'target/**/*.war', followSymlinks: false)
        }

      }
      steps {
        sh 'mvn clean package'
      }
    }

  }
}