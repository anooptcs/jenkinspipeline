pipeline {
    agent any
	
	stage{
		stage('build'){
		sh 'mvn clean package'
		}
		post {
			sucess {
			echo 'Now Archiving...'
			archiveArtifacrs artifacts: '**/targate/*war'
			}
		}
	}
}
