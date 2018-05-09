pipeline {
    agent any
    stages {
        stage("foo") {
            steps {
                script {
                    env.RELEASE_SCOPE = input message: 'User input required', ok: 'Release!',
                            parameters: [choice(name: 'ENV', choices: 'Dev\nStage\nProd', description: 'What is the release scope?'), choice(name: 'TYPE', choices: 'Relase\nPatch\nProd', description: 'What is the release scope?')]
                }
                echo "${env.RELEASE_SCOPE}"
            }
        }
    }
}
