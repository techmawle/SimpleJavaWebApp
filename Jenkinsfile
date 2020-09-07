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
          script {
            scannerHome =  tool type: 'hudson.plugins.sonar.SonarRunnerInstallation', name: 'SonarScanner-PermNode'
            echo "${scannerHome}"
            sh "${scannerHome}/bin/sonar-scanner"
          }

        }

      }
    }

    stage('Wait for Quality Gate') {
      steps {
        timeout(unit: 'MINUTES', time: 5, activity: true) {
          waitForQualityGate(webhookSecretId: 'f76cad53-7e51-4403-b70f-3c3446d23a7b', abortPipeline: true)
        }

      }
    }

  }
}