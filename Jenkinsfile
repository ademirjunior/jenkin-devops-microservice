//DECLARATIVE
pipeline {
		agent any
		stages {
			stage('Build') {
				steps {
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
