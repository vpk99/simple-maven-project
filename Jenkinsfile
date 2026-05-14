pipeline{

    agent{
        label 'dev-server'
    }

    tools {
     maven 'mymaven'
    }

    stages{

      stage('build'){
 
        steps{
            sh 'mvn clean package'
        }
      
    
      
      
      }

     stage{

        parallel{
            stage('testA'){
                steps{
                    echo 'this is test A'
                }
            }

            stage('testb'){
                steps{
                    echo 'this is test B'
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
