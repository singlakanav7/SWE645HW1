pipeline {
    agent any
    stages {
        stage('Publish') { 
            steps {
                script {
                    docker.withRegistry("", "Docker-hub-ksingla") {
                        def customImage = docker.build("ksingla/swe645-fall2020-hw1")
                        customImage.push()
                    }
                }
            }
        }
		stage('Deploy') {
			steps {
				script {
					rancherRedeploy alwaysPull: true, credential: 'rancher-server', images: 'ksingla/swe645-fall2020-hw1:latest', workload: '<Rancher workload URL>'
				}
			}
		}
    }
}
