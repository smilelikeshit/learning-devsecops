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
                        -Dsonar.projectBaseDir=/var/jenkins_home/workspace/example-app \
                        -Dsonar.sources=web \
                        -Dsonar.login='${USERNAME}' -Dsonar.password='${PASSWORD}' \
                        -Dsonar.host.url=http://sonarqube:9000 \
                        -Dsonar.language=php \
                        -Dsonar.scm.exclusions.disabled=true \
                        -Dsonar.scm.enabled=false -X"
                }
        }
    }
}