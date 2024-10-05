pipeline{
    agent any
    tools{
        maven 'my-maven'
        jdk 'my-jdk'
    }
    stages{
        stage('Clone'){
            steps{
                git url:'https://github.com/gururaj-r123/api-gateway.git',branch:'main'
            }
        }
        stage('Build'){
            steps{
                bat "mvn clean install -DskipTests"
            }
        }
        stage('Test'){
            steps{
                bat "mvn test"
            }
        }
        stage('Deploy'){
            steps{
                bat "docker rm -f my-api-container"
                bat "docker rmi -f my-api-image"
                bat "docker build -t my-api-image ."
                bat "docker run -p 8060:8060 -d --name my-api-container my-api-image"
    
        }
    }
    }
}
