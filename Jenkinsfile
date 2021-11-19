pipeline {
    agent{
        docker {
            image 'node:lts-buster-slim'
            args '-p 3000:3000'
        }
    }
    stages {
		stage('Checkout SCM') {
            steps {
                git 'https://github.com/sebastiankzk/JenkinsDependencyCheckTest'
            }
        }      
		stage('OWASP-Dependency-Check') {
            steps {
                dependencyCheck additionalArguments: '', odcInstallation: 'OWASP-Dependency-Check'
            }
        }
        stage('Deliver') {
            steps {
                sh './jenkins/scripts/deliver.sh'
                input message: 'Finished using the web site? (Click "Proceed" to continue)'
                sh './jenkins/scripts/kill.sh'
            }
        }
    }
}
