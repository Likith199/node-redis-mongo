pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('dp')
	}

	stages {
	    
	    stage('gitclone') {

			steps {
				git  'https://github.com/Likith199/node-redis-mongo.git'
			}
		}

		stage('Build') {

			steps {
				sh 'docker build -t durgaprasad7/node:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}
		
		stage('Push') {

			steps {
				sh 'docker push durgaprasad7/node:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}
