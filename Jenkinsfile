pipeline {
    agent none
    stages {   

        stage('versioning') {
             agent {
                docker { image 'docker pull alpine/git' }
            }
            steps {
               sh 'git version'
            }
        }
    }
}