//DECLARATIVE
pipeline {
		agent any
		// agent { docker { image 'maven:3.6.3' } }
		environment {
			dockerHome = tool 'myDocker'
			mavenHome = tool 'myMaven'
			PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
		}
		stages {
			stage('Checkout') {
				steps {
					sh 'mvn --version'
					sh 'docker version'
					echo "Build"
					echo "$PATH"
					echo "BUILD_NUMBER - $env.BUILD_NUMBER"
					echo "BUILD_ID - $env.BUILD_ID"
					echo "BUILD_TAG - $env.BUILD_TAG"
					echo "BUILD_URL - $env.BUILD_URL"
					echo "JOB_NAME - $env.JOB_NAME"
				}
			}
			stage('Compile'){
				steps {
					sh 'mvn clean compile'
				}
			}
			stage('Test') {
				steps {
					sh "mvn test"
				}
			}
			stage('Integration Test') {
				steps {
					//sh "mvn failsafe: integration-test failsafe:verify"
				}
			}

			stage('Package') {
				steps {
					sh "mvn package -Dskiptests"
				}
			}

			stage('Build Docker Image') {
				steps {
					//docker "build -t in28min/currency-exchange-devops:$env.BUILD_TAG"
					script {
						dockerImage = docker.build("in28min/currency-exchange-devops:${env.BUILD_TAG}")
					}
				}
			}
			stage('Push Docker Image') {
				steps {
					script {
						//local da imagem, id cadastrado no jenkisn 
						docker.withRegistry('', 'dockerhub');
						dockerImage.push();
						dockerImage.push('latest')
					}
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
