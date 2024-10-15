@Library('my_shared_library') _
pipeline {
    agent any
    parameters{

        choice{'name: 'action', choices\ndelete', description: 'Choose create/Destroy'}
    }
    stages {

        when { expression { param.action == 'create' } }

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
            when { expression { param.action == 'create' } }
            
            steps{

                script{
                        
                     mvnTest()   
                }
            }
        }
        stage( 'Integration Test Maven' )
        {
            when { expression { param.action == 'create' } }
            
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
                    statiCodeAnalysis()
                }
            }
        }
    }
}