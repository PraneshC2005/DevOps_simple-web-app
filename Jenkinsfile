pipeline {
    agent any

    stages {
        stage('SCM') {
            steps {
                git branch: 'main', url: 'https://github.com/PraneshC2005/DevOps_simple-web-app.git'
            }
        }
        stage('Build') {
            steps{
                sh 'mvn clean'
		sh 'mvn install'
            }
        }
        stage('build to images') {
            steps {
            script{
                sh "docker build -t praneshc/webapplication1 ."
            }
            }
        }
        stage('docker push hub') {
            steps {
            script{
               withDockerRegistry(credentialsId: 'cred-2', url: 'https://index.docker.io/v1/') {
                sh 'docker push praneshc/webapplication1'
            }
            }
            }
        }
    }
}
