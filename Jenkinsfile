pipeline{
    agent any
    stages{
        stage('git scm update') {
            steps {
                git url: 'https://github.com/evollivia/jenkins_nodejs.git', branch: 'main'
            }
        }
    stage('Docker build and deploy') {
        steps {
            sh '''
            docker compose up --build -d
            '''
            }
        }
    }
}