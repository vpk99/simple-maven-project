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

             environment {
                   Name  = "Vinayak"
                 }


              }
         
         stage('test'){

            parallel{

                stage('TestA'){
                    steps{
                        echo "this is test A"
                    }

                stage( 'TestB'){
                    steps{
                        echo " this is test B"
                    }
                }
                }
            }

             post {
                success {
                   
                   archiveArtifacts artifacts: '**/target/*.war'
                }
             }

   }

    }

       
        }
        
    


