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
                sh 'docker build -t keerthi-jenkins-task3 .'   
            }
        }

        stage('push ECR'){
            steps{
                withDockerRegistry( [ credentialsId: "ecr:us-east-1:aws-credentials", url: "https://590852515231.dkr.ecr.us-east-1.amazonaws.com" ] ){
                    sh 'docker tag keerthi-jenkins-task3:latest 590852515231.dkr.ecr.us-east-1.amazonaws.com/keerthi-jenkins-task3:latest'
                    sh 'docker push 590852515231.dkr.ecr.us-east-1.amazonaws.com/keerthi-jenkins-task3:latest'
                }  

            }
        }
    }
}
