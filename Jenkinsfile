pipeline {
	    agent any
	    stages {
	        stage('Build') {
	            steps {
	                bat './mvnw clean' 
	            }
	        }
	        stage('Test') {
	            steps {
	                bat './mvnw test' 
	            }
	        }
	         stage('Package') {
	            steps {
	                bat './mvnw package' 
	            }
	        }
	         stage('Deploy') {
	             when {
	                 branch 'master'
	             }
            steps {
                slackSend channel: 'DT5LZP54K', message: "Build Succeeded ${env.JOB_NAME} ${env.BUILD_NUMBER} (<${env.BUILD_URL}|Open>)"
            }
	        }
	    }
	}
