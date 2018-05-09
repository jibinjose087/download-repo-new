pipeline {
    agent any
    stages {
        stage("User Input Section") {
            steps {
                script {
                    env.RELEASE_SCOPE = input message: 'Enter the details', ok: 'Release!',
                            parameters: [choice(name: 'ENV', choices: 'Dev\nStage\nProd', description: 'What is the release scope?'), choice(name: 'TYPE', choices: 'Relase\nPatch\nProd', description: 'What is the release scope?')]
                }
                echo "${env.RELEASE_SCOPE[ENV]}"

            }
        }
        
            stage ('package stage') {
        steps {
          echo "second stage"
          echo "${env.RELEASE_SCOPE}"
          }
        }
    }
}
