pipeline {
    agent any
    
    environment {
        AWS_BIN = '/usr/bin/aws'
    }
    stages {
        stage("Parameterized stage") {
            steps {
            timeout(1) {
                script {
                    env.RELEASE_SCOPE = input message: 'User input required', ok: 'Release!',
                    parameters: [choice(name: 'EnvType', choices: 'Dev\nStage\nProd', description: 'Enter the environment details'), string(defaultValue: '', description: 'Enter the instance type', name: 'InstanceType')]
                }
               }
                echo "${env.RELEASE_SCOPE}"
                sh aws s3 ls
            }
        }
    }
}
