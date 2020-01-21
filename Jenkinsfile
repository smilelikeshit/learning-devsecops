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
                         args '-u root'
                }

                steps {
                    sh 'sonar-scanner \
                        -Dsonar.projectKey=Bfy0qKYZH7xYJajBTfl6fHbuqdniQEgN \
                        -Dsonar.sources=. \
                        -Dsonar.host.url=https://sonarqube.appserver.id \
                        -Dsonar.login=5f2a7a07fef91676acc3fc9cf9538baa82fcf12'
                }
            }
        }
        
    }
}