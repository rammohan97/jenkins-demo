pipeline {
    agent {
        label 'AGENT-1'
    }
    stages {
        stage ('Build') {
            steps { 
                script {
                    sh """
                        echo "Building on ${env.NODE_NAME}"
                    """
                }
            }
        }
        stage ('Test') {
            steps {
                sh """
                    echo 'Testing..'
                """
            }
        }
        stage ('Deploy') {
            steps {
                sh """
                    echo 'Deploying....'
                """
            }
        }
    }
    post {
        always {
            echo 'This will always run'
            cleanWs()
        }
        success {
            echo 'This will run only if successful'
        }
        failure {
            echo 'This will run only if failed'
        }
    }
}