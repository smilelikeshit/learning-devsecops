pipeline {
    agent none
    stages {
        stage('versioning') {
            agent {
                docker { image 'alpine/git' }
            }
            steps {
                sh 'git version'
            }
        }
        
    }
}