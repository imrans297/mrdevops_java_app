@Library('my_shared_library') _
pipeline {
    agent any
    stages {

        stage( 'Git checkout')
        {
            
            steps{

                script{
                        
                     gitCheckout(
                         branch: 'main', // Comma separates parameters
                        url: 'https://github.com/imrans297/mrdevops_java_app.git'
                     )   
                }
            }
        }
        stage( 'Unit Test Maven')
        {
            
            steps{

                script{
                        
                     mvnTest()   
                }
            }
        }
        stage( 'Integration Test Maven' )
        {
            
            steps{

                script{
                        
                      mvnIntegrationTest()
                }
            }
        }
        stage('Static Code Analysis: Sonarqube')
        {
            steps
            {
                script
                {
                    def SonarQubecredentialsId = 'sonarqube-api'
                    statiCodeAnalysis(SonarQubecredentialsId)
                }
            }
        }
    }
}