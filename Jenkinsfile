pipeline{
    agent any
    stages{
        stage('git scm update') {
            steps {
                git url: 'https://github.com/evollivia/jenkins_nodejs.git', branch: 'main'
            }
        }
        stage('docker build and push') {
            steps {
                sh'''
                docker build -t 54.180.229.129:8081/jenkins_nodejs .
                docker push 54.180.229.129:8081/jenkins_nodejs
                '''
            }
        }
    }
}