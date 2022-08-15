pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('Docker-hub-cred')
	}

	stages {

		stage('Build') {

			steps {
				sh 'docker build -t rmrmhm23/2048:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push rmrmhm23/2048:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}