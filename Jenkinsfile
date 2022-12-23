pipeline {
    agent { label 'Master' }
    environment {
    DOCKERHUB_CREDENTIALS = credentials('dockerhub_akshaynr24')
    }
    stages { 
        stage('Docker image build') {
            steps{
            sh 'docker build -t akshaynr24/nginx:$BUILD_NUMBER .'
            }
        }
        stage('run') {
            steps{
                sh 'docker run -d -p 8090:80 akshaynr24/nginx:$BUILD_NUMBER'
        }
    }

        stage('login to dockerhub') {
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('push image') {
            steps{
                sh 'docker push akshaynr24/nginx:$BUILD_NUMBER'
            }
        }
        
        
}
}
