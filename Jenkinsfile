pipeline {
    agent none

     environment {
        PASSWORD = "${env.PASSWORD}"
        USERNAME = "${env.USERNAME}"
    }


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
                         args '-u root --entrypoint=\'\' -v lib-sonar:/usr/src'
                    }
             }

             steps {
                 sh 'sonar-scanner \
                    -Dsonar.projectKey=Bfy0qKYZH7xYJajBTfl6fHbuqdniQEgN \
                    -Dsonar.sources=. \
                    -Dsonar.host.url=https://sonarqube.appserver.id \
                    -Dsonar.login=jenkins -Dsonar.login=“${USERNAME}” -Dsonar.login=“${PASSWORD}” -X'
             }
        }

           
        
    }
}