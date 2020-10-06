//DECLARATED
pipeline {
	agent any
	//agent { docker { image 'maven:3.6.3' } }
	//agent { docker { image 'node:14.13' } }
	environment {
		dockerHome = tool "myDocker"
		mavenHome = tool "myMaven"
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
//		registry = "efleitasch/currency-exchange-devops"
        registryCredential = 'dockerhub_id'
	}
	stages {
		stage('Chekcout') {
			steps {
				sh "mvn --version"
				sh "docker version"
				echo "Build"
				echo "PATH - $PATH"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "BUILD_ID - $env.BUILD_ID"
				echo "BUILD_TAG - $env.BUILD_TAG"
				echo "JOB_NAME - $env.JOB_NAME"
				echo "BUILD_URL - $env.BUILD_URL"
			}	
		}
		stage('Compile') {
			steps{
				sh "mvn clean compile"
			}
		}
		stage('Test') {
			steps {
				sh "mvn test"
			}
		}
		stage('Integration Test') {
			steps {
				sh "mvn failsafe:integration-test failsafe:verify"
			}	
		}
		stage('Package') {
			steps {
				sh "mvn package -DskipTests"
			}	
		}		
		stage('Build Docker Image') {
			steps {
              //"docker build -t efleitasch/currency-exchange-devops:$env.BUILD_TAG"
			  script {
				  docker.build("efleitasch/currency-exchange-devops:${env.BUILD_TAG}")
			  }
			}
		}
		stage('Push Docker Image') {
			steps {
              script {
				  docker.withRegistry('', registryCredential ) {				
					dockerImage.push()				  
				  }			
			  }
			}
		}
	}

	post {
		always {
			echo "Im awesome. I run always"
		}
		success {
			echo "I run when you are successful"
		}
		failure {
			echo "I run when you fail"
		}
		//changed {
		//	echo "Do something when the status changes from failed <-> success"
		//}
	}
    

}


