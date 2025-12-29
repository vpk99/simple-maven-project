pipeline {

    agent {
        label 'dev-server'
    }

    parameters {
        string(name: 'LASTNAME', defaultValue: 'Khot')
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
                sh 'mvn clean package'
                echo "Hello $Name ${params.LASTNAME}"
            }
        }

        stage('test') {
            parallel {

                stage('this is testA') {
                    steps {
                        echo "this is test A"
                    }
                }

                stage('this is testB') {
                    steps {
                        echo "this is test B"
                    }
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
