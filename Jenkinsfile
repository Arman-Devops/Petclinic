pipeline {
    agent any
    tools {
        jdk 'Jdk17'
        maven 'Maven3'
    }
    environment{
        SCANNER_HOME=tool 'sonar-scanner'
    }
    stages {
        stage('Github') {
            steps {
               git branch: 'main', url: 'https://github.com/Arman-Devops/Petclinic.git'
               
            }
        }
        stage('compile') {
            steps {
               sh "mvn clean compile"
            }
           }
        
        stage('build') {
            steps {
               sh "mvn clean package -DskipTests=true" 
            }
        }
  
        stage('Build & Push Docker Image') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'github-cred') {
                         sh "docker build -t petclinic:latest ."
                         sh "docker tag petclinic:latest armanmk2009/petclinic2:1.0"
                         sh "docker push armanmk2009/petclinic2:1.0"
                     }
                } 
            }
        }
        
    }

}
