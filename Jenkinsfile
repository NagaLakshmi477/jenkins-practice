pipeline {
    agent  {
        label 'AGENT-1'
    }
    environment {
        COURSE = 'Jenkins'
    }
// build
    stages {
        stage('Build') {
            steps {
                script {
                    sh """
                        echo "hello build"
                        env
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