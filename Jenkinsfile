pipeline {
	agent any
	stages{
		stage('Build'){
			steps {
				sh 'mvn clean package'
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
	}
}
