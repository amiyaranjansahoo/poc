@Library('jenkins-lib') _
pipeline {
    agent any
    tools {
        maven 'm3'
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
                //tomcat('tomcat','ec2-user','15.206.116.134')
            //}
        //}
        
        stage("Upload to artifact") {
            steps {
                nexusArtifactUploader artifacts: [[artifactId: 'myweb', classifier: '', 
                    file: 'target/myweb', type: 'war']], 
                    credentialsId: 'nexus3', 
                    groupId: 'in.javahome', 
                    nexusUrl: '172.31.37.225:8081', 
                    nexusVersion: 'nexus3', 
                    protocol: 'http', 
                    repository: 'sample-snapshot', 
                    version: '0.0.2-SNAPSHOT'
            }
        }
    }
}
