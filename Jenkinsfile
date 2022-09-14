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
				echo 'docker build'
				sh "docker build . -t amiyaranjansahoo/myimg"
				echo 'push to docker hub'
				withCredentials([string(credentialsId: 'docker-hub', variable: 'docker_passwd')]) {
					sh "docker login -u amiyaranjansahoo -p {docker_passwd}"
				}
				
			}
		}
		
		stage('deploy to client server'){
			steps{
				echo 'deploy to client server'
			}
		}
	}
}
