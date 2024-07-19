pipeline {
	// agent any
	agent {
		docker {
			image 'composer:latest'
		}
	}
	stages {
		// stage('Pull Docker Image'){
		// 	steps {
		// 		script {
		// 			sh 'docker pull composer:latest'
		// 		}
		// 	}
		// }
		stage('Build') {
			steps {
				// sh 'docker pull composer:latest'
				sh 'composer install'
			}
		}
		stage('Test') {
			steps {
                	   sh './vendor/bin/phpunit --log-junit logs/unitreport.xml -c tests/phpunit.xml tests'
            		}
		}
	}
	post {
		always {
			junit testResults: 'logs/unitreport.xml'
		}
	}
}
