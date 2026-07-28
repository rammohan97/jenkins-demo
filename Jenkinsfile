pipeline {
    
    agent {
        label 'AGENT-1'
    }
    environment {
        COURSE_NAME = "Jenkins"
    }
    options {
        timeout(time: 10, unit: 'MINUTES')
        disableConcurrentBuilds()
    }
    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
        booleanParam(name: 'DEPLOY', defaultValue: false, description: 'Deploy this change')
        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    }

    stages {
        stage ('Example_Parameter') {
            steps {
                echo "Hello ${params.PERSON}"
                echo "Biography: ${params.BIOGRAPHY}"
                echo "Deploy value is: ${params.DEPLOY}"
                echo "Choice selected is: ${params.CHOICE}"
                echo "Password is: ${params.PASSWORD}"
            }
        }
        stage ('Build') {
            steps { 
                script {
                    sh """
                        echo "Building on ${env.NODE_NAME}"
                        echo "Course Name is :  ${env.COURSE_NAME}"
                        # sleep 15
                        env
                    """
                }
            }
        }
        stage ('Test') {
            steps {
                sh """
                    echo 'Testing..........'
                """
            }
        }
        stage ('Deploy') {
            /* input { 
                message "Do you want to deploy?"
                ok "Yes, let's deploy!"
                submitter "admin"
            } */
            when {
                expression { "$params.DEPLOY"  }
            }
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