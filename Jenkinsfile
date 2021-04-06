pipeline {
    agent {
        docker {
            image 'python:3.5.1'
        }
    }

    stages {
        stage('test') {
            steps {
                sh 'echo "this is first step"'
                sh '''
                    echo "this is second step"
                '''
                retry(3) {
                    sh 'this is retry'
                }
                timeout(time: 3, unit: 'MINUTES') {
                    sh 'this is timeout'
                }
            }
        }
    }

    post {
        always { echo 'this will always run' }
        success { echo 'this will run only if successful' }
        failure { echo 'this will run only if failed' }
        unstable { echo 'this will run only if the run was marked as unstable' }
        changed { echo 'this will run only if the state of the Pipeline has changed' }
    }
}
