pipeline {

    agent {
        label 'dev-server'
    }

    parameters {
          choice choices: ['dev','prod '], name: 'select_environment'

    }

    environment {
        Name = "Vinayak"
    }

    tools {
        maven 'MyMaven'
    }

    stages {

        stage('build') {
            steps {
                sh 'mvn clean package -DskipTests=true'
                
            }
        }

        stage('test') {
            parallel {
               
                stage('this is testA') {
                    agent{ label 'dev-server'}
                    steps {
                        echo "this is test A"
                        sh "mvn test"
                    }
                }
                
                stage('this is testB') {
                    agent{ label 'dev-server'}
                    steps {
                        echo "this is test B"
                        sh "mvn test"
                    }
                }
            }
        
            post {
            success {
            dir("webapp/target"){
                stash name: "maven-build" , includes: " *.war"
            }
        }
    }

  }
            
           
        
        stage('prod_deploy'){
           
         when { expression {params.select_environment == 'prod'}
        beforeAgent true}
        agent { label 'dev-server' }
        
        steps{
            dir("/var/www/html"){

                unstash "maven-build"
            }

            sh """
            cd /var/www/html
            jar -xvf webapp.war
            """
        }
        }

    
        
   
   
   
   
   
   
   
    }


    

    
} 
