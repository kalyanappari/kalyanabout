pipeline{

    agent any

    environment{
        image = 'kalyan3003/about'
    }

    stages{
        stage('Clone repo'){
            steps{
                git branch: 'main',url: 'https://github.com/kalyanappari/kalyanabout.git'
            }
        }
        stage('Build Image'){

            steps{
                script{
                    docker_image = docker.build("${image}:latest")
                }
            }

        }
        stage('Deploy to hub'){
            steps{
                script{
                    docker.withRegistry('https://index.docker.io/v1/','DockerHUB'){
                       docker_image.push();
                    }
                }
            }
        }
    }
}
