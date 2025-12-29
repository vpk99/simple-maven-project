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

        stage('test'){

            parallel{

                stage('this is testA'){

                    steps{
                        echo "this is test A "
                    }
                }

                stage('this is testB'){

                    steps{

                        echo "this is test b"
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

       
        
        
    


