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
		stage('Build'){
			steps {

				echo 'PATH $PATH'
				sh 'mvn --version'
				sh 'docker version'
				sh 'PATH $PATH'
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