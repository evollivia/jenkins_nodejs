pipeline {
    agent any
    environment {
        DOCKERHUB_SECRETS=credentials('dockerhub')
        IMAGE_NAME="docdker/jenkins_nodejs4"
        IMAGE_TAG="latest"
    }
    stages {
        stage('clone from SCM') {
            steps {
                git url: 'https://github.com/evollivia/jenkins_nodejs.git', branch: 'main'
            }
        }
        stage('Docker building Node.js App') {
            steps {
                sh '''
                docker compose build
                '''
            }
        }
        stage('Logging into Docker Hub') {
            steps {
                sh'''
                echo ${DOCKERHUB_SECRETS_PSW} | docker login -u ${DOCKERHUB_SECRETS_USR} --password-stdin
                '''
            }
        }
        stage('Pushing Docker image to Docker Hub') {
            steps {
                sh'''
                docker tag docdker/nodejs-app ${IMAGE_NAME}:${IMAGE_TAG}
                docker push ${IMAGE_NAME}:${IMAGE_TAG}
                '''
            }
        }
        stage('Docker Hub Logout') {
            steps {
                sh'''
                docker logout
                '''
            }
        }
        stage('Docker Hub Image remove') {
            steps {
                sh'''
                docker rmi ${IMAGE_NAME}:${IMAGE_TAG}
                '''
            }
        }
    }
}
