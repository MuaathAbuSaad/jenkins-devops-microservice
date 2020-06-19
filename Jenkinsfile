//scripted pipeline
// node {
// 		echo "Build"
// 		echo "Test"
// 		echo "Integration Test"
// 	}

//Declarative pipeline

pipeline {
	agent {
        docker { image 'maven:3.6.3' }
    }
	stages {
		stage('Build'){
			steps {
				sh 'mvn --version'
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