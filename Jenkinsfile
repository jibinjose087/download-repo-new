pipeline {
    agent any
    
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
            }
        }
        
       stage("AWS stage") {
        steps {
            sh aws s3 ls
        }
    }
        
        
        
    }
}
