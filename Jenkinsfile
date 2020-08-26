pipeline {
    agent any
    parameters {
          string(defaultValue: 'RDBJOB', description: 'Enter version', name: 'VERSION')
    }
    stages {
        stage ('Build'){
            steps {
                sh "Echo ${VERSION}"
            }
        }
    }
} 