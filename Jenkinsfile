pipeline {
  agent any
  stages {
    stage('Launch FrontEnd Pipeline') {
      when {
        true
      }
      steps {
        build job: 'FrontEmployeePipeline'
      }
    }
    stage('Launch BackEnd Pipeline') {
      when {
        changeset "EmployeeProjectBack/"
      }
      steps {
        build job: 'BackEmployeePipeline'
      }
    }
  }
}