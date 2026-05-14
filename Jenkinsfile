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
      
        post{
            sucess{
                archiveArtifacts artifacts: '**/target/*.war'
            }
        }
      
      
      }



    

}


}
