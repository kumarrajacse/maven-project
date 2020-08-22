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
		
		stage('SonarQube analysis') {
withSonarQubeEnv('sonar')
{
sh 'mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.6.0.1398:sonar'
}
}
}
}	
