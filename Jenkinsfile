pipeline {
    agent any 
    options {
    skipDefaultCheckout true
  }
    stages {
        stage('First stage') {
            steps {
                eho 'Hello, Maven'
            }
        }
        stage('Second stage') {
            steps {
                echo 'Hello, JDK'
            }
        }
    }
    
        post { 
        always { 
            echo 'I will always say Hello again!'
        }
        changed { 
            echo 'Previous one is success but this one failed'
        }
    }
    
}
