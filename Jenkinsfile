pipeline {
	agent any
	stages{
		stage('Build'){
			steps {
				def mvnHome = tool name: 'maven-3.5.4', type: 'maven'
				def mvnCMD = "${mvnHome}/bin/mvn"
				sh "${mvnCMD} clean package"
			}
			post {
				success {
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
