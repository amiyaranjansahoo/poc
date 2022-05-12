pipeline {
    agent any
    tools {
        maven 'maven3'
    }
    stages {
        //stage("Git clone") {
            //steps {
             //   git credentialsId: 'git_cred', url: 'https://github.com/amiyaranjansahoo/poc.git'
            //}
        //}
        
        stage("Build the source code using maven") {
            steps {
                sh 'mvn clean package'
            }
        }
        
        //stage("SCP the artifcat and deploy to tomcat") {
            //steps {
                //sshagent(['tomcat']) {
                   // sh 'scp -o StrictHostKeyChecking=no target/myweb.war ec2-user@172.31.12.198:/software/tomcat9/webapps/'
                	//sh 'ssh ec2-user@172.31.12.198 /software/tomcat9/bin/shutdown.sh'
                	//sh 'ssh ec2-user@172.31.12.198 /software/tomcat9/bin/startup.sh'
                //}
            //}
        //}
    }
}
