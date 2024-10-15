@Library('my_shared_library') _
pipeline {
    agent any
    stages {

        stage( 'Git checkout')
        {
            
            steps{

                script{
                        
                     gitCheckout(
                        branch: "main"
                        url: "https://github.com/imrans297/mrdevops_java_app.git"
                     )   
                }
            }
        }
    }

        
}