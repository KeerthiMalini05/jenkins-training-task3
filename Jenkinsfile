pipeline {
    agent any

    stages {
        stage('build'){
            steps{
            sh 'mvn clean package'
            }
        }

        stage('deploy'){
            steps{
                sh 'docker build -t hariv-jenkins-task3:latest .'   
            }
        }

        stage('push ECR'){
            steps{
                withDockerRegistry( [ credentialsId: "ecr:us-east-1:aws.credentials", url: "https://590852515231.dkr.ecr.us-east-1.amazonaws.com" ] ){
                    sh 'docker tag hariv-jenkins-task3:latest 590852515231.dkr.ecr.us-east-1.amazonaws.com/hariv-jenkins-task3:$BUILD_NUMBER'
                    sh 'docker push 590852515231.dkr.ecr.us-east-1.amazonaws.com/hariv-jenkins-task3:$BUILD_NUMBER'
                }  

            }
        }
    }
}