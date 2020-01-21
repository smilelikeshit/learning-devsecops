pipeline {
    agent none
    stages {
        stage('versioning') {
            agent {
                docker { image 'alpine:latest' }
            }
            steps {
                sh 'apk add git'
                sh 'git version'
            }
        }
        
    }
}