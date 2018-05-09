pipeline {
    agent any
    stages {
        stage("User Input Section") {
            steps {
                script {
                env.RELEASE_SCOPE = input message: 'Enter the details', ok: 'Release!',
                        parameters: [choice(name: 'ENV', choices: 'Dev\nStage\nProd', description: 'What is the Environment?')]
                env.APP_SCOPE = input message: 'Enter the details', ok: 'Release!',
                        parameters: [choice(name: 'APP', choices: 'Release\nDeploy\nProd', description: 'What is the release scope?')]                    

        }
                echo "${env.RELEASE_SCOPE}"

            }
        }
        
            stage ('package stage') {
        steps {
          echo "second stage"
          echo "${env.APP_SCOPE}"
          }
        }
    }
}
