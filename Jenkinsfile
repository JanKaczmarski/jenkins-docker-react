pipeline {
    agent any
    environment {
        dockerimagename = "bigjack213/docker-react"
        dockerImage = ""
    }
    stages {
        stage ('Checkout source') {
            steps {
                git 'https://github.com/JanKaczmarski/jenkins-docker-react.git'
            }
        }

        stage ('Build image') {
            steps{
                script{
                    dockerImage = docker.build(dockerimagename, "-f Dockerfile.dev .")
                }
            }
        }
        stage ('Run test') {
            steps {
                script {
                    dockerImage.run('npm run test')
                }
            }
        }
        
    }
}