pipeline {
    agent none

     environment {
        PASSWORD = "${env.PASSWORD}"
        USERNAME = "${env.USERNAME}"
        PROJECTKEY = "${env.PROJECTKEY}"
        URL_SERVER = "${env.URL_SERVER}"
    }


    stages {

        agent any
        /* stage('versioning') {
            agent {
                docker { image 'alpine:latest' 
                         args '-u root'
                }
            }
            steps {
                sh 'apk add git'
                sh 'git version'
            }
        } */

        stage('SonarQube analysis') {

            
             def scannerHome = tool 'sonarscanner';
             steps {
                    withSonarQubeEnv('sonar-server') {
                     sh "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=example \
                        -Dsonar.sources=web \
                        -Dsonar.host.url=http://172.19.0.7:9000 \
                        -Dsonar.login=f895dc668a278fdefd52819c07453cd05c2b810e" 
                }

             }
        }  
        
    }
}