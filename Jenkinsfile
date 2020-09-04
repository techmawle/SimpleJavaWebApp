pipeline {
  agent any
  stages {
    stage('Build') {
      post {
        always {
          echo 'I will always say Hello again!'
        }

      }
      steps {
        sh 'mvn clean package'
      }
    }

  }
}