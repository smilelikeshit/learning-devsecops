pipeline {
    agent none
    
    // - menggunakan ip karena error apabila memanggil service 'sonarqube' padahal masih di networks yang sama
    // - ip dapat di isi dengan ip yang di terdapat di container sonarqube atau ip host 
    // - sebagai contoh sekarang saya menggunakan ip pada host/laptop yang terassign dari wifi
    environment {
        IP_ADDRESS = "x.x.x.x"
    }
    stages {
        stage('build') {
           agent {
                docker { image 'alpine:latest' 
                         args '-u root'
                }
            }
            steps {
                sh 'echo "ini stage stage build"'
                
            }
        }

        stage('unit test') {
           agent {
                docker { image 'alpine:latest' 
                         args '-u root'
                }
            }
            steps {
                sh 'echo "ini stage unit test"'
                
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
                        -Dsonar.login='admin' -Dsonar.password='admin' \
                        -Dsonar.host.url=http://${IP_ADDRESS}:9000 \
                        -Dsonar.language=php \
                        -Dsonar.scm.exclusions.disabled=true \
                        -Dsonar.scm.enabled=false -X"
                }
        }
    }
}