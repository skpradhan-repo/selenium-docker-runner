pipeline{
	agent any
	stages{
		stage("Build Grid"){
			steps{
				sh "docker-compose up -d hub"
			}
		}
		stage("Run Test"){
			steps{
				sh "docker-compose up search-module book-flight-module"
			}
		}
		stage("Bring Grid Down"){
			steps{
				sh "docker-compose down"
			}
		}
	}
}
