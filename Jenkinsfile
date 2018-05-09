def UserInput
pipeline {
    agent any
    stages {
        stage("User Input Section") {
            steps {
                script {
                UserInput = input message: 'Enter the details', ok: 'Release!',
                        parameters: [choice(name: 'ENV', choices: 'Dev\nStage\nProd', description: 'What is the Environment?'), choice(name: 'APP', choices: 'Release\nDeploy\nProd', description: 'What is the release scope?')]
        }
                echo "${UserInput.ENV}"

            }
        }
        
            stage ('package stage') {
        steps {
            echo "${UserInput.APP}"
          }
        }
    }
}
