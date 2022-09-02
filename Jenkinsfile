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

	environment {
		dockerHome = tool 'myDocker'
		mavenHome = tool 'myMaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}

	stages {
		stage('Rookie'){
			steps {
				sh 'mvn --version'
				// sh 'node --version'
				sh 'docker version'
				echo "BlackAgumon"
				echo "PATH - $PATH"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "BUILD_ID - $env.BUILD_ID"
				echo "JOB_NAME - $env.JOB_NAME"
				echo "BUILD_TAG - $env.BUILD_TAG"
				echo "BUILD_URL - $env.BUILD_URL"
			}
		}
		// stage('Champion'){
		// 	steps{
		// 		echo "Tyrannomon"
		// 	}
		// }
		// stage('Perfect'){
		// 	steps{
		// 	echo "MasterTyrannomon"	
		// 	}
		// }
		stage('Compile'){
			steps{
				sh "mvn clean compile"
			}
		}

		stage('Test'){
			steps{
				sh "mvn test"
			}
		}

		stage('Integration Test'){
			steps{
				sh "mvn failsafe:integration-test failsafe:verify "
			}
		}

		stage('Package'){
			steps{
				sh "mvn package -DskipTests"
			}
		}

		stage ('Build Docker Image')
		{
			steps{
				//"docker build -t krishnandu360/currency-exchange-devops:$env.BUILD_TAG"
				script{
					dockerImage = docker.build("krishnandu360/jenkins-devops-microservice:${env.BUILD_TAG}")
				}
			}
		}

		stage ('Push Docker Image')
		{
			steps{
				script{
					docker.withRegistry('','DockerHub')
					dockerImage.push();
					dockerImage.push('latest');
				}
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
	
	
	
