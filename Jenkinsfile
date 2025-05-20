pipeline {
    agent any 
    environment {
    DOCKERHUB_CREDENTIALS = credentials('amonkincloud-dockerhub')
    }
    stages { 

        stage('Build docker image') {
            steps {  
                sh 'sudo docker build -t laksmikanthare905/flaskapp:$BUILD_NUMBER .'
            }
        }
        stage('login to dockerhub') {
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('push image') {
            steps{
                sh 'docker push laksmikanthare905/flaskapp:$BUILD_NUMBER'
            }
        }
}
post {
        always {
            sh 'docker logout'
        }
    }
}
