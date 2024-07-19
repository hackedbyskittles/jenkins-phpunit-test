pipeline {
	agent any
	// agent {
	// 	docker {
	// 		image 'composer:latest'
	// 	}
	// }
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
				sh 'apt-get update'
                           	sh 'apt-get install -y php-cli php-mbstring unzip '     
        			sh 'curl -sS https://getcomposer.org/installer|php -- --install-dir=/usr/local/bin --filename=composer'
				// sh 'apt-get update'
    //                     	sh 'apt-get install -y php8.2-mysql php8.2-gd php8.2-curl unzip default-mysql-client nodejs npm '

				// sh 'curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer'

				// sh 'composer install --no-interaction --prefer-dist'  
    //                     	sh 'composer update mews/captcha --no-interaction --prefer-dist'
    //                     	sh 'composer update --dev orchestra/testbench --no-interaction --prefer-dist'

				// sh 'docker pull composer:latest'
				// sh 'composer install'
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
