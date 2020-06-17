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
}