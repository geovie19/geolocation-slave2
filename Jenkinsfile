pipeline {
    agent any
    tools{
        maven 'M2_HOME'
    }
    environment {
        registry = '676334272140.dkr.ecr.us-east-1.amazonaws.com/ernesto'
        dockerimage = ''
    } 

    stages {
        stage('Checkout'){
            steps{
                git branch: 'main', url: 'https://github.com/geovie19/geolocation-slave2.git'
            }
        }
    }   
        stage('Code Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        // Building Docker images
        stage('Building image') {
            steps{
                script {
                    dockerImage = docker.build registry
                }
            }
        }
        // Uploading Docker images into AWS ECR
        stage('Building image') {
            steps{
                script {
                    dockerImage = docker.build registry
                }
            }
        }
        // Uploading Docker images into AWS ECR
        stage('Pushing to ECR') {
            steps{
                script {
                    sh 'aws ecr get-login-password --region us-east-1 | docker login --username geovie19 --password-stdin 676334272140.dkr.ecr.us-east-1.amazonaws.com'

                              sh 'docker push 676334272140.dkr.ecr.us-east-1.amazonaws.com/ernesto' 
                         }
            }              
        }
        
             
    }                

}
