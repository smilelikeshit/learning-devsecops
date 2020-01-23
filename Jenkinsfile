pipeline {
    agent any

     environment {
        PASSWORD = "${env.PASSWORD}"
        USERNAME = "${env.USERNAME}"
        PROJECTKEY = "${env.PROJECTKEY}"
        URL_SERVER = "${env.URL_SERVER}"
    }


    stages {
        stage('versioning') {
           /* agent {
                docker { image 'alpine:latest' 
                         args '-u root'
                }
            } */
            steps {
                sh 'echo "HELLO WOLRD"'
                
            }
        

        /*stage('SonarQube analysis') {

            
             def scannerHome = tool 'sonarscanner';
             steps {
                    withSonarQubeEnv('sonar-server') {
                     sh "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=example \
                        -Dsonar.sources=web \
                        -Dsonar.host.url=http://172.19.0.7:9000 \
                        -Dsonar.login=f895dc668a278fdefd52819c07453cd05c2b810e" 
                }

             } */
        }  
        
    }
}