@Library('jenkins-lib') _
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
        
        stage("SCP the artifcat and deploy to tomcat") {
            steps {
                tomcat('tomcat','ec2-user','15.206.116.134')
            }
        }
    }
}
