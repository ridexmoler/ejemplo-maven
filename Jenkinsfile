pipeline {
    agent any

    stages {
        stage('Compile Code') {
            steps {
                dir("/Users/procco/personal/usach/Modulo3/repositorios/ejemplo-maven"){
                    sh './mvnw clean compile -e'   
                }
            }
        }
        
        stage('Test Code') {
            steps {
                dir("/Users/procco/personal/usach/Modulo3/repositorios/ejemplo-maven"){
                    sh './mvnw clean test -e'   
                }
            }
        }
        
        stage('Jar Code') {
            steps {
                dir("/Users/procco/personal/usach/Modulo3/repositorios/ejemplo-maven"){
                    sh './mvnw clean package -e'   
                }
            }
        }
        
        stage('Run Jar') {
            steps {
                dir("/Users/procco/personal/usach/Modulo3/repositorios/ejemplo-maven"){
                    sh 'nohup bash mvnw spring-boot:run &'   
                }
            }
        }
        
        stage('Testing Application') {
            steps {
                dir("/Users/procco/personal/usach/Modulo3/repositorios/ejemplo-maven"){
                    sleep 20
                    sh "curl -X GET 'http://localhost:8081/rest/mscovid/test?msg=testing'" 
                }
            }
        }
        
    }
}