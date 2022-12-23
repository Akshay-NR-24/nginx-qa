pipeline {
    agent { label 'cproj' } 
    environment {
    DOCKERHUB_CREDENTIALS = credentials('docker-nginx')
    }
    stages { 
        stage('Build docker image') {
            steps {  
                sh 'docker build -t manasabhat2222/nginx:$BUILD_NUMBER .'
            }
        }
        stage('login to dockerhub') {
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('push image') {
            steps{
                sh 'docker push manasabhat2222/nginx'
            }
        }
        stage('RUN') {
        steps {
        sh 'docker run -d -p 8000:80 manasabhat2222/nginx:$BUILD_NUMBER'
        }
        }
        }
}
