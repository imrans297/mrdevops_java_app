@Library('my_shared_library') _
pipeline {
    agent any
    parameters{

        choice(name: 'action', choices: 'create\ndelete', description: 'Choose create/Destroy')
    }
    stages {

        stage( 'Git checkout')
        {
            when { expression { params.action == 'create' } }
            
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
            when { expression { params.action == 'create' } }
            
            steps{

                script{
                        
                     mvnTest()   
                }
            }
        }
        stage( 'Integration Test Maven' )
        {
            when { expression { params.action == 'create' } }
            
            steps{

                script{
                        
                      mvnIntegrationTest()
                }
            }
        }
        stage('Static Code Analysis: Sonarqube')
        {
            when { expression {  params.action == 'create' } }
            steps
            {
                script
                {
                    def SonarQubecredentialsId = 'Sonar-Qube'                      
                    statiCodeAnalysis(SonarQubecredentialsId)
                }
            }
        }
    }
}