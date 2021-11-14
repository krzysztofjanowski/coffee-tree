pipeline {
    agent any
    environment {
        RELEASE='20.04'
    }
    stages {
        stage('Build') {
            agent any
            environment {
                LOG_LEVEL='INFO'
            }
            steps {
                echo "Building release ${RELEASE} with log level ${LOG_LEVEL}..."
                echo "one echo after another works fine..."
            }
        }
        stage('Test') {
            steps {
                echo "Testing release ${RELEASE}..."
            }
        }
        stage('Deploy') {
            steps {
                echo "Deploying release ${RELEASE} to environment ${TARGET_ENVIRONMENT}"
            }
        }        
    }
    post{
        always {
             echo 'Prints whether deploy happened or not, success or failure'
             slackSend channel: '#general',
                       message: 'release: ${RELEASE} has been deployed '
        }
    }
}