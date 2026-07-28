pipeline {
    
    agent {
        label 'AGENT-1'
    }
    environment {
        COURSE_NAME = "Jenkins"
    }
    options {
        timeout(time: 10, unit: 'SECONDS')
    }

    stages {
        stage ('Build') {
            steps { 
                script {
                    sh """
                        echo "Building on ${env.NODE_NAME}"
                        echo "Course Name is :  ${env.COURSE_NAME}"
                        sleep 15
                        env
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
        aborted {
            echo 'This will run only if pipeline aborted'
        }
    }
}