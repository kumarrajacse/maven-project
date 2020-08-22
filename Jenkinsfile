pipeline {
    agent any

    parameters {
         string(name: 'tomcat', defaultValue: 'localhost', description: 'tomcat Server')
         
    }

    
stages{
        stage('checkout'){
		   steps{
		   git 'https://github.com/kumarrajacse/maven-project.git'
		   }
		}		   
        stage('Build'){
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }

        /*stage ('Deployments'){
            parallel{
                stage ('Deploy to tomcat server'){
                    steps {
                        sh "scp -i  **/target/*.war /var/lib/tomcat7/webapps"
                    }
                }
            }
        }
    }*\
}
