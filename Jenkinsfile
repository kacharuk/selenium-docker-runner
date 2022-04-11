pipeline{
	agent any
	stages{
    stage("Pull Latest Image"){
      steps{
        bat "docker pull kacharuk/selenium-docker"
      }
    }
		stage("Start Grid"){
			steps{
				bat "docker-compose up -d hub chrome firefox"
			}
		}
		stage("Run Test"){
			steps{
				bat "docker-compose up search-module1 book-flight-module1"
			}
		}
	}
  post{
    always{
      archiveArtifacts artifacts: 'output/**'
      bat "docker-compose down"
    }
  }
}