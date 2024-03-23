pipeline{
    agent any
    tools{
        jdk 'Jdk-17'
        maven 'Maven-3'
    }
    stages{
        stage('checkout scm'){
            steps{
                git branch:'main',url:'https://github.com/Arman-Devops/Petclinic.git'
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
        stage('deploy to tomcat'){
            steps{
                deploy adapters: [tomcat9(credentialsId: 'tomcat-cred',
                 path: '',
                 url: 'http://52.2.10.18:8080')],
                 contextPath: null,
                 war: '**/*.war'
            }
        }
    }
}
