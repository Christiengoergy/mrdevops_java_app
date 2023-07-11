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
        stage('unit test mvn'){

            steps{
               script{
                mvnTest()
               }
                }
            }    
    }
}

