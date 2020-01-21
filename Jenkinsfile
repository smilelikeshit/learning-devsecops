pipeline {
    agent none
    stages {   

        stage('versioning') {
             agent {
                docker { image 'alpine:latest' }
            }
            steps {
               sh 'uname -a'
            }
        }
    }
}