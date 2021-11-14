pipeline {
   agent any
    environment {
      RELEASE='20.04'
    }
   stages {
      stage('Pre-deploy') {
            environment {
               LOG_LEVEL='INFO'
            }
            steps {
               echo "Building release ${RELEASE} with log level ${LOG_LEVEL}..."
               }
            }
        }
        stage('Test') {
            steps {
               echo "Testing release ${RELEASE}"
               writeFile file: 'test-results.txt', text: 'passed'               
            }
        }
   }
   post {
      success {
         archiveArtifacts 'test-results.txt'
         slackSend channel: '#general',
                   message: "finished"
      }
   }
}