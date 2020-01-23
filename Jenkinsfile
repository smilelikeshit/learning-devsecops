pipeline {
    agent none

     environment {
        PASSWORD = "${env.PASSWORD}"
        USERNAME = "${env.USERNAME}"
        PROJECTKEY = "${env.PROJECTKEY}"
        URL_SERVER = "${env.URL_SERVER}"
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
                        -Dsonar.projectKey=example \
                        -Dsonar.sources=. \
                        -Dsonar.host.url=http://172.19.0.7:9000 \
                        -Dsonar.login=f895dc668a278fdefd52819c07453cd05c2b810e \
                        -Dsonar.login="admin" -Dsonar.password="admin" -X'
               
             }

             post {
                 always {
                        archiveArtifacts artifacts: '/usr/src/.scannerwork/', fingerprint: true

                 }
             }


        }  
        
    }
}