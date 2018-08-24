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
	}
}
