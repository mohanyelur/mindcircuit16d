pipeline {
    agent any

    stages {
        stage('Git clone') {
            steps {
                echo 'cloning code from github'
				git branch: 'main', url: 'https://github.com/mohanyelur/mindcircuit16d.git'
            }
        }
		
		stage('Maven build') {
            steps {
                echo 'Build using the maven'
				sh 'mvn clean install'
            }
        }
		
		stage('Deploy into tomcat') {
            steps {
                echo 'Deploying using tocat webserver'
				deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'tomcat', path: '', url: 'http://ec2-98-82-2-186.compute-1.amazonaws.com:8080/')], contextPath: 'favdrfjj', onFailure: false, war: '**/*.war'
            }
        }
    }
}
