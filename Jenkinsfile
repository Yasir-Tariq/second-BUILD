pipeline {
    agent any
    parameters {
          string(defaultValue: 'RDBJOB', description: 'Enter version', name: 'VERSION')
    }
    stage('Build rds-util') {
      when {
        expression { env.BRANCH_NAME == "staging/dev" || env.BRANCH_NAME ==~ "staging/v.*" } 
      }
      steps {
        script {
          if (env.BRANCH_NAME == "staging/dev") {
            build job: '../rdb-util', wait: false, parameters: [
              [$class: 'StringParameterValue', name: 'VERSION', value: 'dev']
            ]
          }
          if (env.BRANCH_NAME ==~ "staging/v.*") {
            build job: '../rdb-util', wait: false, parameters: [
              [$class: 'StringParameterValue', name: 'VERSION', value: env.BRANCH_NAME.substring(8)] 
            ]
          }
        }
      }
    }
} 
