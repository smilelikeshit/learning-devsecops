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
                sh 'echo "HELLO WOLRD"'
                
            }
        }

        stage('SonarQube analysis') {            
            agent {
                docker {
                    image 'newtmitch/sonar-scanner:4.0.0'
                    args '-u root --entrypoint=\'\' -v lib-sonar:/root/.sonar/'
                }
            }
            
             steps {
                    
                     sh "sonar-scanner \
                        -Dsonar.projectKey=example-app \
                        -Dsonar.sources=. \
                        -Dsonar.login='admin' -Dsonar.password='admin' \
                        -Dsonar.host.url=http://172.19.0.7:9000 \
                        -Dsonar.login=example \
                        -Dsonar.language=php \
                        -Dsonar.scm.exclusions.disabled=true -X"
                }
        }
         
        
    }
}