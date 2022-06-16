pipeline {
	agent any
	tools {
	  maven 'maven3'
	}
	
	stages {
		stage('Build the project using maven') {
			steps {
				sh 'mvn clean package'
			}
		}
		
		stage('Create the docker image') {
			steps {
				sh "docker build . -t amiyaranjansahoo/docker-img-weekend:${latestCommitID()}"
			}
		}
		
		stage('Push the image to docker hub') {
			steps {
				withCredentials([string(credentialsId: 'docker-hub', variable: 'dockerPWD')]) {
					sh "docker login -u amiyaranjansahoo -p ${dockerPWD}"
					sh "docker push amiyaranjansahoo/docker-img-weekend:${latestCommitID()}"
				}
			}
		}
		
		stage('Transfer and Deploy the image to dev server') {
			steps {
				sshagent(['docker-dev']) {
    sh "ssh -o StrictHostKeyChecking=no ec2-user@172.31.33.242 docker container rm -f myweb"
	sh "ssh -o StrictHostKeyChecking=no ec2-user@172.31.33.242 docker container run -itd -p 9090:8080 --name myweb amiyaranjansahoo/docker-img-weekend:${latestCommitID()}" 
}
			}
		}
	}
}



def latestCommitID() {
	def latestCommitID=sh returnStdout: true, script: 'git rev-parse --short HEAD'
	return latestCommitID
}
