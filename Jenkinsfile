pipeline {
	agent any
	tools {
		maven 'mvn'
	}

	
	stages{
		stage('git clone'){
			steps{
				git credentialsId: 'git_cred', url: 'https://github.com/amiyaranjansahoo/poc'
			}
		}
		
		stage('maven build'){
			steps{
				sh 'mvn clean package'
			}
		}
		
		stage('docker build and push to docker hub'){
			steps{
				echo 'docker build and push to docker hub'
			}
		}
		
		stage('deploy to client server'){
			steps{
				echo 'deploy to client server'
			}
		}
	}
}
