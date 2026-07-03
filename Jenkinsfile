pipeline {
    agent  {
        label 'AGENT-1'
    }
    environment {
        COURSE = 'Jenkins'
    }
    options {
        timeout(time: 1,unit: 'MINUTES')
        disableConcurrentBuilds()
        }
         parameters {
        string(name: 'DEPLOY_TAG', defaultValue: 'latest', description: 'The Git tag to deploy')
        choice(name: 'TARGET_ENV', choices: ['development', 'staging', 'production'], description: 'Select environment')
        booleanParam(name: 'RUN_TESTS', defaultValue: true, description: 'Check to execute test suite')
    }
// build
    stages {
        stage('Build') {    
            steps {
                script {
                    sh """
                        echo "hello build"
                        sleep 10    
                        env
                        echo "Deploying version ${params.DEPLOY_TAG} to ${params.TARGET_ENV}..."
                    """
                    }
            }
        }

        stage('Test') {
            steps {
                echo 'Testing...'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying...'
            }
        }
        
    }
    // Post section it will run pipline is sucess
    // we need to delete data after running pipeline
    post {
        always {
            echo 'I will always say hello'
            deleteDir()
        }
        success {
            echo 'hello success'
        }
         failure {
            echo 'hello failure'
        }
    }
}