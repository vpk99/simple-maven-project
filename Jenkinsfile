pipeline {
   
   parameters {
     string defaultValue: 'Khot', name: 'LASTNAME'
    }

     environment {
    Name  = "Vinayak"
   }

   agent {
      label 'dev-server'
     }

    tools {
       maven 'MyMaven'
    }

    stages {

        stage('build'){
            
            steps{
                sh 'mvn clean package'
                echo " HellO $Name ${params.LASTNAME}"
            }

            post {
            success {
                   
                   archiveArtifacts artifacts: '**/target/*.war'
               }
             }


        }

       
        }
        }
    


