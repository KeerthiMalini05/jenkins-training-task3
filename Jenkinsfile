pipeline {
    agent any

    stages {
        stage('create jar'){
            steps{
            sh 'mvn clean package'    
            sh 'java -jar target/spring-boot-web.jar'
            }
        }

        stage('build'){
            steps{
                sh 'docker run -d -p 8080:8080 -t spring-boot:1.0'
            }
        }
    }
}