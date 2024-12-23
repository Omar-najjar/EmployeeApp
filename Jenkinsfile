pipeline {
  agent any
  stages {
    stage('Launch FrontEnd Pipeline') {
      when {
        expression {
                    return true // The condition is always true
                }
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