pipeline {
	agent any
	stages{
		stage('Build'){
			steps {
				sh 'mvn clean package'
			}
			post {
				seccuss {
					echo 'Now archiving...'
					archiveArtifacts artifacts: '**/*.war'
				}
			}
		}
		stage ('Deploye to stageing'){
			steps{
				build job: 'Deploy-to-staging'
			}
		}
	
		stage ('Deploye to prod'){
				steps{
					timeout(time:5, unit:'DAYS'){
						input message: 'Approve PROD Deployment?'
					}
				
					build job: 'Deploy-to-Prod'
				}
			post {
				success {
					echo 'Code Deployed to Prod'
				}
				failure {
					echo 'Deployment Failed'
					}
				}
			}
	}
}
