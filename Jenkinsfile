pipeline {
    agent any
 
    tools {
        maven 'localMaven'
    }
 
stages{
        stage('Build'){
            steps {
                 build job: 'packagedemo'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
		
		stage ('static analysis'){
			
			steps {
			build: 'static analysis'
			}
		
		}
		stage ('Deploy to Staging'){
            
            steps {
                
                build job: 'Deploy-to-staging'
            }
        }
				stage ('Deploy to Prod'){
		           
		            steps {
		            
		                build job: 'Deploy-to-Prod'
            }
        }
    }
 }
   