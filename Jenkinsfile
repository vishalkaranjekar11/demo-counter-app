pipeline{
    agent any
    
    stages{
        stage("Git Checkout"){
            steps{
                git branch: 'main', url: 'https://github.com/vishalkaranjekar11/demo-counter-app.git'
            }
            
        }
        stage("Unit Testing"){
            steps{
                sh 'mvn test'
            }
            
        }
         stage("Integration testing"){
            steps{
                sh 'mvn verify -DskipUnitTest'
            }
            
        }
        stage("Maven Build"){
            steps{
                sh 'mvn clean install'
            }
            stage("SonarQube analysis"){
            steps{
                withSonarQubeEnv(credentialsId: 'sonar-api') {
                 sh 'mvn clean package sonar:sonar'
               }
            }
            
          }
        
        }
    }
    
}