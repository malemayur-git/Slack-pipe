pipeline {
	agent any
	triggers {
  		pollSCM '* * * * *'
	}
	
	stages {
	    stage('Checkout') {
	        steps {
			checkout scm			       
		      }}
		stage('Build') {
	           steps {
			  sh '/home/mayur/Documents/DevOps-Software/apache-maven-3.9.6/bin/mvn install'
	                 }}
		stage('Deployment'){
		    steps {
			script {
			 if ( env.ENV == 'QA' ){
        	sh 'cp target/Slack-pipe.war /home/mayur/Documents/DevOps-Software/apache-tomcat-9.0.79/webapps'
        	echo "deployment has been COMPLETED on QA!"
			 }
			else ( env.ENV == 'UAT' ){
    		sh 'cp target/PIPELINE.war /home/swapnil/Documents/DevOps-Software/apache-tomcat-9.0.79/webapps'
    		echo "deployment has been done on UAT!"
			}
			}}}	
stage(slack') {
    steps {
       slackSend baseUrl: 'https://hooks.slack.com/services/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/', channel: 'ramtek', color: 'good', message: 'xyz', teamDomain: 'Student', tokenCredentialId: '5c396f00-a103-4837-9452-dd71e5a6c367'}
}
}}
