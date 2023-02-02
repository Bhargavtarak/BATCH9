pipeline {
    agent any

    stages {
        stage('CLONE SCM STAGE') {
            steps {
                echo 'cloning code from github'
				git branch: 'main', credentialsId: 'githubcredentials', url: 'https://github.com/Bhargavtarak/BATCH9.git'
            }
        }
		
		stage('BUILD ARTIFACT STAGE') {
            steps {
                echo 'show the source code'
				sh 'ls'
				echo 'build using maven'
				sh 'mvn clean install'
            }
        }
		
		stage('DEPLOY TO TOMCAT STAGE') {
            steps {
                echo 'deploy to tomcat application server'
				deploy adapters: [tomcat9(credentialsId: '20f5b72e-14ab-4b70-9c23-c4f10480f45c', path: '', url: 'http://54.71.195.140:8081/')], contextPath: 'FACEBOOK', war: '**/*.war'
            }
        }
    }
}
