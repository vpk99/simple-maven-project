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
            sh 'mvn build package'
          }
        }

        post {
         
          success {
              archiveArtifacts artifacts: '**/target/*.war'
      }
   }

    }

}