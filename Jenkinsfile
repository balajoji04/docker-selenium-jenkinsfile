pipeline {
    agent any
    
    stages { 	
        stage('Build Jar') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }
        stage('Build Image') {
            steps {
                script {
                	app = docker.build("bala19/docker-test")
                }
            }
        }
        stage('Push Image') {
            steps {
                script {
			        docker.withRegistry('https://hub.docker.com', 'dockerhub') {
			        	app.push("${BUILD_NUMBER}")
			            app.push("latest")
			        }
                }
            }
        }        
    }
}
