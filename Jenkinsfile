@Library('jenkins_shared_lib') _
pipeline{
    agent any

    stages{
        stage('Git chwechout'){

            steps{
               gitCheckout(
                branch: "main",
                url: "https://github.com/Christiengoergy/mrdevops_java_app.git"
            )
                }
            }
        stage('Unit Test maven'){

            steps{
               script{
                  mvnTest()
               }
            }
        }
        stage('Integration Test maven'){

            steps{
               script{
                  mvnIntegrationTest()
               }
            }
        }    
    }
}

