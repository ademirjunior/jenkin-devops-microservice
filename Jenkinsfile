//DECLARATIVE
pipeline {
		//agent any
		agent { docker { image 'maven:3.6.3' } }
		stages {
			stage('Build') {
				steps {
					esh 'mvn --version'
					echo "Build"
				}
			}
			stage('Test') {
				steps {
					echo "Test"
				}
			}
			stage('Integration Test') {
				steps {
					echo "Integration Test"
				}
			}
		} 
		
		post {
			always {
				echo 'Message always printed.'
			}
			success {
				echo 'Message printed when successfull'
			}
			failure {
				echo 'Message printed when fails'
			}
		} 
}
