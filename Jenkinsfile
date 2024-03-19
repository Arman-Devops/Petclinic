pipeline{
    agent any
    tools{
        jdk 'Jdk-17'
        maven 'Maven-3'
    }
    stages{
        stage('checkout scm'){
            steps{
                git branch:'main',url:'git@github.com:Arman-Devops/Petclinic.git'
            }
        }
        stage('compile'){
            steps{
                sh 'mvn clean compile'
            }
        }
        stage('build'){
            steps{
                sh 'mvn clean package'
            }
        }
    }
}
