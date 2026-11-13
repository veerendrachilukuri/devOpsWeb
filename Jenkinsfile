pipeline{
    agent any
    stages{
        stage('Clone'){
            steps{
              git branch: 'feature/2026.10.14', url: 'https://github.com/veerendrachilukuri/devOpsWeb.git'
            }
        }
        stage('Build'){
            steps{
                bat 'mvn install'
            }
        }
        stage('Test'){
 
            steps{
 
                bat 'mvn test'
            }
        }
        stage('Published Artifcats'){
 
            steps{
 
                archiveArtifacts artifacts: 'target/*.war', followSymlinks: false
            }
        }
        stage('Deploy'){
 
            steps{
 
              deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'TomcatCredentials', path: '', url: 'http://localhost:8080/')], contextPath: 'DevOPsWeb', war: 'target/*.war'
            }
        }
    }
}