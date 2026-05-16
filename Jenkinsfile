pipeline{

    agent{
        label 'dev-server'
    }

    tools {
     maven 'mymaven'
    }

    parameters {
      choice choices: ['dev', 'prod'], name: 'select_env'
    }


    stages{

      stage('build'){
 
        steps{
            sh 'mvn clean package -DskipTests=true'
        }
      
    
      
      
      }

     stage('test'){

        parallel{
            
           
            stage('testA'){
                 agent{ label 'dev-server'}
                steps{
                    echo 'this is test A'
                    sh 'mvn test'
                }
            }

            stage('testb'){
               
                agent{label 'dev-server'}
                steps{
                    echo 'this is test B'
                    sh 'mvn test'
                }
            }
        }

            post {
         
            success {
              
              dir("webapp/target"){

                stash name: "maven-build" , includes:"*.war"
              }
            }
          }

     }

      stage('deploy-dev'){
        when{expression {params.select_env == 'dev'} 
        beforeAgent true}
        agent{label 'dev-server'}

        steps
        {
            dir("/var/www/html"){

                unstash "maven-build"
            }
            sh """
            cd /var/www/html/
            jar -xvf webapp.war
            """
        }
      }

    
     stage('deploy-prod')
     {
       when{expression {params.select_env == 'prod'} 
        beforeAgent true}
        agent{label 'prod-server'}


        steps
        {  
            timeout(time:5, unit:'DAYS'){
                input message:'Deployment approved?'
            }
            dir("/var/www/html"){

                unstash "maven-build"
            }
            sh """
            cd /var/www/html/
            jar -xvf webapp.war
            """
        } 
     }



    

}


}
