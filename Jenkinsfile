pipeline {
	agent any
	parameters {
		string(name:'U_NAME', defaultValue:'', description:'enter the dockerhub user name')
		password(name:'PWD', defaultValue:'', description:'enter the password')
	}
	environment {
		DOCKER_IMAGE = "santhoshsp/py-pro:v${BUILD_NUMBER}"
	}
	stages {
		stage('git checkout') {
			steps {
				git credentialsId: 'git-2', url: 'https://github.com/Arun02136/san-task2.git'
			}
		}
		stage('build docker image') {
			steps {
				bat "docker build -t ${env.DOCKER_IMAGE} ."
			}
		}
		stage('push to dockerhub') {
			steps {
				bat "docker login -u ${params.U_NAME} -p ${params.PWD}"
				bat "docker push ${env.DOCKER_IMAGE}"
			}
		}
	}
}
