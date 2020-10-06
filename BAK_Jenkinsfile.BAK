//SCRIPTED
// node {
//     echo "Build"
// 	echo "Test"
// 	echo "Integration Test"
// }

//DECLARATED
pipeline {
	agent any
	//agent { docker { image 'maven:3.6.3' } }
	//agent { docker { image 'node:14.13' } }
	stages {
		stage('Build') {
			steps {
				//sh "mvn --version"
				//sh "node --version"
				echo "Build"
				echo "PATH - $PATH"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "BUILD_ID - $env.BUILD_ID"
				echo "BUILD_TAG - $env.BUILD_TAG"
				echo "JOB_NAME - $env.JOB_NAME"
				echo "BUILD_URL - $env.BUILD_URL"
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

//Pipelines
//checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/efleitasch/jenkin-devops-microservice/']]])

//catchError(message: 'Do something') {
    // some block
//}

//input 'I would want you to enter something'

//retry(5) {
    // some block
//}

//sleep time: 10, unit: 'NANOSECONDS'

//timeout(time: 300, unit: 'SECONDS') {
    // some block
//}
