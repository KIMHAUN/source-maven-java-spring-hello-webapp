pipeline {
	agent any

	triggers {
		pollSCM('* * * * *')
	}

	stages {
		stage('Checkout') {
			steps {
				git branch: 'main',
				url: 'https://github.com/KIMHAUN/source-maven-java-spring-hello-webapp.git'
			}
		}
		stage('Build') {
			steps {
				bat 'mvn clean package'
			}
		}
		stage('Deploy') {
			steps {
				deploy adapters: [tomcat9(credentialsId: 'tomcat-manager', url: 'http://localhost:8070')], contextPath: null, war: 'target/hello-world.war'
			}
		}
	}
}
