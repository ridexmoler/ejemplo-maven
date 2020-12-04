pipeline {
    agent any

    stages {
        stage('Compile Code') {
            steps {
                sh './mvnw clean compile -e'   
            }
        }
        
        stage('Test Code') {
            steps {
                sh './mvnw clean test -e'   
            }
        }
        
        stage('Jar Code') {
            steps {
                sh './mvnw clean package -e'   
            }
        }

        stage('SonarQube') {
            withSonarQubeEnv(installationName: 'sonar_local') { // You can override the credential to be used
                sh 'mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.7.0.1746:sonar'
            }
        }
        
        stage('Run Jar') {
            steps {
                sh 'nohup bash mvnw spring-boot:run &'   
            }
        }
        
        stage('Testing Application') {
            steps {
                sleep 20
                sh "curl -X GET 'http://localhost:8081/rest/mscovid/test?msg=testing'" 
            }
        }
        
    }
}
