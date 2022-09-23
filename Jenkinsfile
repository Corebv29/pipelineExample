//CODE_CHANGES = getGitChanges()
pipeline {

    agent any
    tools{
        maven 'Maven'
    }
    parameters{
        string(name: 'Version', defaultValue: '', description: 'version to deploy on prod')
        choice(name: 'VERSION', choices['1.0.0','1.0.1','1.0.2'], description: 'Choices to take')
        booleanParam(name: 'executeTests', defaultValue: true, description: 'The description')
    }
    environment{
        NEW_VERSION = '1.3.0'
        //SERVER_CREDENTIALS = credentials('server-credentials') // Credentials binding plugin
    }
    stages{

        stage("build"){
         /*   when{
                expression{
                    env.BRANCH_NAME == 'master' && env.CODE_CHANGES == true
                }
            }*/
            steps{
                echo 'Building application'
                echo "Building version ${NEW_VERSION}"
            }
        }
        stage("test"){
          /*  when{
                expression{
                    env.BRANCH_NAME == 'dev' || env.BRANCH_NAME == 'master'
                }
            }*/
            when{
                expression{
                   params.executeTests == true
                }
            }
            steps{
                echo 'Testing application'
            }
        }
        stage("deploy"){
            steps{
                echo 'Deploying application'
                //echo "Deploying with ${SERVER_CREDENTIALS}"
                //sh "${SERVER_CREDENTIALS}"
                echo "Deploying version ${params.VERSION}"
                // Credentials Plugin
                // Credentials Binding
             /*   withCredentials([
                    usernamePassword(credentials: 'server-credentials', usernameVariable: USER, passwordVariable: PWD)
                ]){
                    sh "some script ${USER} ${PWD}"
                }*/
            }
        }
    }
/*    post{
        always{

        }
        success{

        }
        failure{

        }
    }*/
}