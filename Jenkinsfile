pipeline {
	agent any 
	
	triggers {
  pollSCM '* * * * *'
}
	parameters {
  choice choices: ['DEV', 'QA', 'UAT'], name: 'environment'
}
	stages {
	    stage('Checkout') {
	        steps {
			checkout scm			       
		      }}
		stage('Build') {
	           steps {
			  sh '/home/akash/Documents/apache-maven-3.9.6/bin/mvn install'
	                 }}
		stage('Deployment'){
		   steps {
		sh 'cp target/GRRAS.war /home/akash/Documents/apache-tomcat-9.0.88/webapps'
			}}
		stage('slack-notification'){
		   steps {
		     
		     slackSend baseUrl: 'https://hooks.slack.com/services/', channel: 'devops-class', color: 'good', message: 'Welcome to Jenkins', notifyCommitters: true, teamDomain: 'GRRAS', tokenCredentialId: '699a073c-76c5-497b-9553-daabdbd536f5'
		     }}	
}}
