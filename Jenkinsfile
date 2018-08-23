	pipeline {
		agent any
		stages{
			stage('Build'){
			sh 'mvn clean package'
			}
			post {
				sucess{
					echo 'Now Archiving...'
					archiveArtifacrs artifacts: '**/targete/*war' 
				}
			}
		}
		stage('Deploye to stageing'){
			steps {
				build job:'Deploy-to-staging'
			}
		}
	
	}
  

