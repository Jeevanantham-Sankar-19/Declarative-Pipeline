pipeline {
    agent any 
    stages {
        stage('Continous Download'){
            steps{
                script {
                    try{
                        git branch: 'main', url: 'https://github.com/Jeevanantham-Sankar-19/Maven-Tomcat.git'

                    }
                    catch(Exception e){
                        echo "Git clone failed: ${e.message}"
                        currentBuild.result = 'FAILURE'
                        error("Stopping pipeline due to git clone failure.")
                    }
                }
            }
        }
        stage('Continous Build'){
            steps{
                script {
                    try{
                        sh 'mvn package'
                    }
                    catch (Exception e){
                        echo "Build failed: ${e.message}"
                        currentBuild.result = 'FAILURE'
                        error("Stopping pipeline due to build failure.")
                    }
                }
            }
        }
        stage('Continous Test'){
            steps{
                script {
                    try{
                        deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'Tomcat-Prod-Server', path: '', url: 'http://54.174.8.189:8080')], contextPath: 'petshop/test', war: '**/*.war'
                    }
                    catch (Exception e){
                        echo "Test failed: ${e.message}"
                        currentBuild.result = 'FAILURE'
                        error("Stopping pipeline due to test failure.")
                    }
                }
            }
        }
    }
}