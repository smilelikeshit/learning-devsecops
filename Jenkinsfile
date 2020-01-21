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
                         args '-u root --entrypoint=\'\''
                    }
             }

            steps {
                    sh 'sonar-scanner \
                        -Dsonar.projectKey=Bfy0qKYZH7xYJajBTfl6fHbuqdniQEgN \
                        -Dsonar.sources=. \
                        -Dsonar.host.url=https://sonarqube.appserver.id \
                        -Dsonar.login=723c85972859a9b17a489d4086fff7f6aab04bbb'
            }
        }
        
    }
}