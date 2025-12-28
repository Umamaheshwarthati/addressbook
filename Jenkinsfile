pipeline {
   agent any
   tools {
      tool name: 'jdk', type: 'jdk'
      tool name: 'maven', type: 'maven'
   }
    parameters {
        string(name: 'Environment', defaultValue: 'test', description: 'The Environment to build for')
        booleanParam(name: 'ExecuteTests', defaultValue: true, description: 'Execute the Tests')
        choice(name: 'APP_VERSION', choices: ['1.0.0', '1.0.1', '1.0.2'], description: 'The Application Version to build for DEV, QA, PROD')
    }
    stages {
        stage('Compile') { //prod
        
            steps {
                script {
                   echo "Compile the code"
                   echo "Test the code : ${params.Environment}"
                   sh "mvn complie"
                }
            }
        }
         stage('UnitTest') { //test
         when{
            expression {
                params.ExecuteTests == true
            }
           }
            steps {
                script {
                   echo "Test the code : ${params.Environment}"
                   sh "mvn test"
                }
            }
        }
         stage('Package') {//dev
       
            steps {
                script {
                   echo "Package the code"
                   echo "Package the code version: ${params.APP_VERSION}"
                   sh "mvn package"
                }
            }
        }
       stage('Deploy') {//dev
            input {
               message "Select the version to deploy"
               ok "version selected"
               parameters {
                  choice (name: 'NEWVERSION', choices :['3.2','3.3','3.4'])
               }
            }
            steps {
                script {
                echo "Deploy the App"
                echo "Deploy the code version: ${params.APP_VERSION}"
                }
            }
        }
    }
}
