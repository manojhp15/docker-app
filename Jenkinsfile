pipeline{
    agent any
    environment{
        DOCKER_HUB = credentials('docker-pwd')
    }
    stages{
        stage("Downloading from SCM"){
            steps{
                git 'https://github.com/manojhp15/docker-app.git'
            }
         }
        stage("Building the war"){
            steps{
                sh 'mvn clean package'
            }
        }
        stage('Build Docker Image'){
            steps{
                sh 'docker build -t manojnike15/my-app:2 .'
              }
        stage('Push docker image'){
            steps{
                sh 'docker login -u manojnike15 -p ${DOCKER_HUB}'
                sh 'docker push manojnike15/my-app:2'
            }

        }
        }

        }
    }
