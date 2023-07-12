@Library('jenkins_shared_lib') _
pipeline{
    agent any
    parameters{

        choice(name: 'action', choices: 'create\ndelete', description: 'Choose create/Destroy')
        choice(name: 'Project', description: 'dockerimagename', defaultValue: 'javaapp')
        choice(name: 'ImageTag', description: 'dockerimagetag', defaultValue: 'v1')
        choice(name: 'hubUser', description: 'dockerusername', defaultValue: 'christiengoergy')
    }
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
        stage('Static code analysis:sonarqube'){
                     when { expression {  params.action == 'create' } }
            steps{
               script{
                def SonarQubecredentialsId = 'sonar-api'
                statiCodeAnalysis(SonarQubecredentialsId)
               }
            }
        } 
        stage('Quality Gate status check :sonarqube'){
                     when { expression {  params.action == 'create' } }
            steps{
               script{
                def SonarQubecredentialsId = 'sonar-api'
                QualityGateStatus(SonarQubecredentialsId)
               }
            }
        }
        stage('dockerbuild'){
                     when { expression {  params.action == 'create' } }
            steps{
               script{
                dockerBuild("${params.Project}","${params.ImageTag}","${params.HubUser}")
               }
            }
        }              
    }
}

