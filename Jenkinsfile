pipeline {
    agent none

     environment {
        PASSWORD = "${env.PASSWORD}"
        USERNAME = "${env.USERNAME}"
        PROJECTKEY = "${env.PROJECTKEY}"
        URL = "${env.URL}"
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
                        -Dsonar.projectKey="${PROJECTKEY}" \
                        -Dsonar.sources=./dvwa \
                        -Dsonar.host.url="${URL}" \
                        -Dsonar.login=jenkins -Dsonar.login="admin" -Dsonar.password="${PASSWORD}" -X'
               
             }

             post {
                 always {
                        archiveArtifacts artifacts: '/usr/src/.scannerwork/report-task.txt', fingerprint: true

                 }
             }


        }  
        
    }
}