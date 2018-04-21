pipeline {
  agent any
  stages {
    stage('Test') {
      parallel {
        stage('Pester') {
          steps {
            powershell(script: 'Invoke-Pester -Path "$env:workspace\\add-numbers.test.ps1"', returnStatus: true)
            nunit(testResultsPattern: 'pester-output.xml', failIfNoResults: true)
          }
        }
        stage('PSScriptAnalyzer') {
          steps {
            powershell(script: 'Invoke-ScriptAnalyzer -Path "$env:workspace\\add-numbers.psm1"', returnStatus: true)
          }
        }
      }
    }
    stage('Publish to Nexus') {
      steps {
        powershell(script: 'write-host "hi"', returnStatus: true, returnStdout: true)
      }
    }
  }
}