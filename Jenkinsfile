// node {
// 	stage('Build') {
// 		echo "Build"
// 	}
// 	stage('Test') {
// 		echo "Test"
// 	}
// 	stage('Integration Test'){
// 		echo "Integration Test"
// 	}
// }


// node {
// 		echo "Build"
// 		echo "Test"
// 		echo "Integration Test"	
// }

// DECLARATIVE
pipeline{
	agent any
	// agent {docker{image 'maven:3.6.3'}}
	// agent {docker {image 'node:13.8'}}

	stages {
		stage('Rookie'){
			steps {
				// sh 'mvn --version'
				sh 'node --version'
				echo "BlackAgumon"
				echo "PATH - $PATH"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "BUILD_ID - $env.BUILD_ID"
				echo "JOB_NAME - $env.JOB_NAME"
				echo "BUILD_TAG - $env.BUILD_TAG"
				echo "BUILD_URL - $env.BUILD_URL"
			}
		}
		stage('Champion'){
			steps{
				echo "Tyrannomon"
			}
		}
		stage('Perfect'){
			steps{
			echo "MasterTyrannomon"	
			}
		}
	}
	
	post {
		always {
			echo 'BlackAgumon Digivolution.'
		}
		success{
			echo 'Evolution reached to Perfect level.'
		}
		failure{
			echo 'Digivolution failed.'
		}
	}
}
	
	
	
