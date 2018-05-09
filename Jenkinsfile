def UserInput
pipeline {
    options {
    buildDiscarder(logRotator(numToKeepStr: '5', daysToKeepStr: '1'))
    }
    agent any
    stages {
        stage("User Input Section") {
            steps {
            script {
            UserInput = input message: 'Enter the details', ok: 'Release!',
            parameters: [choice(name: 'ENV', choices: 'Dev\nStage\nProd', description: 'What is the Environment?'), string(defaultValue: '', description: 'Enter the Stack Name', name: 'STACK_NAME'), string(defaultValue: '', description: 'Enter the application Name', name: 'APP'), choice(name: 'SSDevopsInstanceType', choices: 't2.micro', description: 'What is the release scope?')]
            }
            echo "${UserInput.ENV}"

            }
        }

        stage ('package stage') {
            steps {
            build job: 'Cloudformation-Dev-Job-Status-check', parameters: [string(name: 'STACK_NAME', value: 'UserInput.STACK_NAME')], propagate: false, quietPeriod: 60
            }
        }

        stage ('STACK_NAME stage') {
            steps {
            echo "${UserInput.STACK_NAME}"
            }
        }
    }

    post {
        changed { 
        echo 'Current build is success'
        }
        failure { 
        echo 'Previous one is success but this one failed'
        }
        always { 
        echo 'Email sent successfully'
        }
    }
}
