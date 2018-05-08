pipeline {
    agent any
    stages {
        stage("foo") {
            steps {
                script {
                    env.RELEASE_SCOPE = input message: 'User input required', ok: 'Release!',
                    parameters: [choice(name: 'EnvType', choices: 'Dev\nStage\nProd', description: 'Enter the environment details'), string(defaultValue: 'AppName', description: 'Enter the instance type', name: 'InstanceType')]
                }
                echo "${env.RELEASE_SCOPE}"
            }
        }
    }
}
