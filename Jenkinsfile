pipeline {
  agent {
    node {
      label 'plain,maven'
    }

  }
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