pipeline {
	agent any
    	environment {
        	CI = 'true'
    	}
	stages {
		stage('Checkout SCM') {
			steps {
				git 'https://github.com/sebastiankzk/JenkinsDependencyCheckTest'
			}
		}
		stage('OWASP DependencyCheck') {
			steps {
				dependencyCheck additionalArguments: '--format HTML --format XML', odcInstallation: 'OWASP-Dependency-Check'
			}
		}
	}	
	post {
		success {
			dependencyCheckPublisher pattern: 'dependency-check-report.xml'
		}
	}
}
