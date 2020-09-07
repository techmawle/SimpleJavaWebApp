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

    stage('Sonar Analysis') {
      steps {
        withSonarQubeEnv(installationName: 'OnHost-SonarQubeServer', credentialsId: 'f76cad53-7e51-4403-b70f-3c3446d23a7b', envOnly: true) {
          sh '${scannerHome}/bin/sonar-scanner'
        }

      }
    }

  }
}