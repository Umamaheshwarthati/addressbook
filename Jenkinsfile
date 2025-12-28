pipeline {
   agent any
   
    stages {
        stage('Compile') { //prod
        
            steps {
                script {
                echo "Compile the code"
                }
            }
        }
         stage('UnitTest') { //test
         
            steps {
                script {
                echo "Test the code"
                }
            }
        }
         stage('Package') {//dev
       
            steps {
                script {
                echo "Package the code"
                }
            }
        }
    }
}
