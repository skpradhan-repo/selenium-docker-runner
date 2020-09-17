pipeline{
	agent any
	stages{
		stage("Delete Existing Project"){
			sh "sudo rm -r /home/centos8/jenkins/workspace/selenium-docker-runner"
		}
		stage("Pull Latest Image"){
			steps{
				sh "docker pull samareshpro/selenium-docker"
			}
		}
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
	}
	post{
		always{
			archiveArtifacts artifacts: 'output/**'
			sh "docker-compose down"
		}
	}
}
