pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t image03 .'
            }
        }
        stage ("Tag") {
            steps {
                sh 'docker tag image03 joshi2106/paytm:moviess'
            }
        }
        stage('Push') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerhub') {
                      sh 'docker push joshi2106/paytm:moviess'
                    }
                }
            }
        }
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name movieapplication -p 3333:80 joshi2106/paytm:moviess'
            }
        }
    }
}
