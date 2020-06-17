//scripted pipeline
// node {
// 		echo "Build"
// 		echo "Test"
// 		echo "Integration Test"
// 	}

//Declarative pipeline

pipeline {
	agent any
	stages {
		stage('Build'){
			steps {
				echo "Building Steps"
			}
		}
		stage('Test') {
			steps {
				echo "Testing steps"
			}
		}
		stage('Integration Test'){
			steps {
				echo "Integration Test steps"
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