pipeline {
    agent any
    parameters {
          string(defaultValue: 'RDBJOB', description: 'Enter version', name: 'VERSION')
    }
    stages {
        stage ('BRANCH'){
            steps {
                script{
                    sh "git rev-parse --abbrev-ref HEAD"
                    sh "echo ${env.BRANCH_NAME}"
                }
            }
        }
        stage('Build rds-util') {
          when {
            expression { env.BRANCH_NAME == "staging/dev" || env.BRANCH_NAME ==~ "staging/v[0-9].*" } 
          }
          steps {
            script {
              if (env.BRANCH_NAME == "staging/dev") {
                build job: '../RDB', wait: false
              }
                if (env.BRANCH_NAME ==~ "staging/v[0-9].*") { 
                sh "echo SECONDDDDDDDDDD"
                build job: '../RDB', wait: false
              }
                else {
                    sh "echo ELSE BLOCK"
                }
            }
          }
        }
    }
} 
