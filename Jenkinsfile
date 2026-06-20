pipeline {
    agent any 
    stages {
        stage('Continous Download'){
            steps{
                git branch: 'main', url: 'https://github.com/Jeevanantham-Sankar-19/Maven-Tomcat.git'
            }
        }
        stage('Continous Build'){
            steps{
                sh 'mvn package'
            }
        }
        stage('Continous Test'){
            steps{
                deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'Tomcat-Prod-Server', path: '', url: 'http://98.80.74.138:8080')], contextPath: 'petshop/test', war: '**/*.war'
            }
        }
    }
}