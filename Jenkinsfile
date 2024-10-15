@Library('my-shared-library')
pipeline {
    agent any
    stages {

        stage( 'Git_checkout')
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