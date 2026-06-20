pipeline {
    agent any 
    stages {
        stage('Continous Download'){
            steps{
                git branch: 'main', url: 'https://github.com/Jeevanantham-Sankar-19/spring-framework-petclinic.git'
            }
        }
        stage('Continous Build'){
            steps{
                sh 'mvn package'
            }
        }
        stage('Continous Test'){
            steps{
                deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'Tomcat-Prod-Server', path: '', url: 'http://http://18.212.83.50:8080')], contextPath: 'petshop/test', war: '**/*.war'
            }
        }
    }
}