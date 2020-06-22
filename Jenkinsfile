//scripted pipeline
// node {
// 		echo "Build"
// 		echo "Test"
// 		echo "Integration Test"
// 	}

//Declarative pipeline

pipeline {
	agent any
	// agent {
    //     docker { image 'maven:3.6.3' }
    // }

	environment {
		dockerHome = tool 'dockerLocal'
		mavenHome = tool 'mavenLocal'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	stages {
		stage('Checkout'){
			steps {

				echo 'PATH $PATH'
				sh 'mvn --version'
				sh 'docker version'
				echo "Building Steps"
			}
		}
		
		stage('Compile') {
			steps {
				sh "mvn clean compile"
			}
		}
		
		stage('Test') {
			steps {
				sh "mvn test"
			}
		}
		stage('Integration Test'){
			steps {
				sh "mvn failsafe:integration-test failsafe:verify"
			}
		}

		stage('Package'){
			steps {
				sh "mvn package -DskipTests"
			}
		}

		stage('Build Docker image'){
			steps {
				//docker build -t mumoali/currency-exchange-devops:${env.BUILD_TAG}
				script{
					dockerImage = docker.build("mumoali/currency-exchange-devops:${env.BUILD_TAG}")
				}

			}
		}

		stage('Push Docker image'){
			steps {
					script {
						docker.withRegistry('','dockerhub') {
							dockerImage.push();
							dockerImage.push('latest');
					}
				}
			}
		}
	}
	post {
		always {
			echo "I run always"
		}
		success {
			echo "I run when success"
		}
		failure {
			echo "I run when failure"
		}
	}
}