pipeline {
    agent none
    stages {
        stage('versioning') {
            agent {
                docker { image 'alpine:latest' 
                         args '-u root'
                }
            }
            steps {
                sh 'apk add git'
                sh 'git version'
            }
        }
        stage('SonarQube analysis') {
             agent {
                docker { image 'newtmitch/sonar-scanner:alpine' 
                         args '-u root --entrypoint=\'\' -v $(pwd):/usr/src'
                    }
             }

            steps {
                    sh 'sonar-scanner \
                    -Dsonar.projectKey=Bfy0qKYZH7xYJajBTfl6fHbuqdniQEgN \
                    -Dsonar.sources=. \
                    -Dsonar.host.url=https://sonarqube.appserver.id \
                    -Dsonar.login=jenkins -X'
                                }
        }
        
    }
}