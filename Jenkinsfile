pipeline {
   
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

            }

            post {
            success {
                   
                   archiveArtifacts artifacts: '**/target/*.war'
               }
             }


        }

       
        }
        }
    


