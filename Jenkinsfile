pipeline{

    agent any

    environment{

        DOCKER_TAG = getDockerTag()

    }

    stages{

        stage('Build Docker Image'){

            steps{

                sh "docker build . -t rajasekhar11022/helloimage:${DOCKER_TAG}"
            }
        }

        stage('DockerHub Push'){

            steps{

                withCredentials([string(credentialsId: 'docker-hub', variable: 'dockerHubPwd')]) {

                    sh "docker login -u rajasekhar11022 -p ${dockerHubPwd}"

                    sh "docker pull rajasekhar11022/helloimage:34505bec364b7c7cba92221a73e9c8a431bf4262"
                }
            }
        }

    }




}

def getDockerTag(){

    def tag = sh script:'git rev-parse HEAD', returnStdout: true

    return tag
}