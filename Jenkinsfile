//DECLARATIVE
pipeline {
		agent any
		// agent { docker { image 'maven:3.6.3' } }
		stages {
			stage('Build') {
				steps {
					// sh 'mvn --version'
					echo "Build"
					echo "$PATH"
					echo "BUILD_NUMBER - $env.BUILD_NUMBER"
					echo "env.BUILD_ID"
					echo "env.BUILD_TAG"
					echo "env.JOB_NAME"
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
