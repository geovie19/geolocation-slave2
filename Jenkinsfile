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
                git branch: 'main', url: 'https://github.com/geovie19/geolocation-slave.git'
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
                    sh 'aws ecr get-login-password --region us-east-1 | docker login --username geovie19 --password-Mich2008$
         2551558.dkr.ecr.us-east-1.amazonaws.com'
                              sh 'docker push 076892551558.dkr.ecr.us-east-1.amazonaws.com/geolocation_ecr_rep:latest' 
                         }
            }              
        }
        //deploy the image that is in ECR to our EKS cluster
             
                    
