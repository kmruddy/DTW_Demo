pipeline {
  agent any
  stages {
    stage('Pester') {
      steps {
        powershell(script: './add-numbers.test.ps1', returnStatus: true)
      }
    }
    stage('Create Manifest') {
      steps {
        sh 'echo "hello"'
      }
    }
    stage('Publish to Nexus') {
      steps {
        sh 'echo "hello"'
      }
    }
  }
}