pipeline {
  agent any
  stages {
    stage('Test') {
      parallel {
        stage('Pester') {
          steps {
            powershell(script: 'Invoke-Pester -Path "$env:workspace\\add-numbers.test.ps1"', returnStatus: true)
          }
        }
        stage('PSScriptAnalyzer') {
          steps {
            powershell 'Import-Module C:\\Program Files\\WindowsPowerShell\\Modules\\PSScriptAnalyzer\\1.16.1\\PSScriptAnalyzer.psm1'
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