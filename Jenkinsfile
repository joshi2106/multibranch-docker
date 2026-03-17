pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t image01 .'
            }
        }
        stage ("Tag") {
            steps {
                sh 'docker tag image01 joshi2106/paytm:bank'
            }
        }
        stage('push') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerhub') {
                      sh 'docker push joshi2106/paytm:bank'
                   }
                }
            }
       }
       stage ("Deploy") {
          steps {
                sh 'docker run -itd --name bankapplication  -p 1111:80 joshi2106/paytm:bank'
            }
        }
    }
}
