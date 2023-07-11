@Library('jenkins_shared_lib') _
pipeline{
    agent any

    stages{
        stage('Git chwechout'){
                   when { expression {  params.action == 'create' } }

            steps{
               gitCheckout(
                branch: "main",
                url: "https://github.com/Christiengoergy/mrdevops_java_app.git"
            )
                }
            }
        stage('Unit Test maven'){
                        when { expression {  params.action == 'create' } }
            steps{
               script{
                  mvnTest()
               }
            }
        }
        stage('Integration Test maven'){
                      when { expression {  params.action == 'create' } }

            steps{
               script{
                  mvnIntegrationTest()
               }
            }
        }
        stage('Staticcode Analysis'){
                            when { expression {  params.action == 'create' } }
            steps{
               script{
                  statiCodeAnalysis()
               }
            }
        }        
    }
}

