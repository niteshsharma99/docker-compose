#!groovy

pipeline {
  agent none
  stages {
    stage('Maven Install') {
	agent any
      	steps {
		sh 'mvn -f ./first/pom.xml clean install'
      	}
    }
    stage('Docker Build') {
      agent any
      steps {
        sh 'docker-compose build'
	sh 'docker-compose up -d'
      }
    }
	stage ('Docker Push') {
      agent any
      steps {
        withDockerRegistry([ credentialsId: "dockerhub_id", url: "" ]) {
          sh 'docker push nitesh99sharma/hello-world:4.0'
        }
      }
	}
  }
}
