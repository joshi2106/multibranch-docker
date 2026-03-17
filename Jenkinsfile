pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t image2 .'
            }
        }
        stage ('tag') {
            steps {
                sh 'docker tag image2 joshi2106/paytm:buses'
            }
        }
        stage('Push') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerhub') {
                      sh 'docker push joshi2106/paytm:buses'
                      }
                }
            }
        }
        stage ('deploy') {
            steps {
                sh 'docker run -itd --name busapplication -p 2222:80 joshi2106/paytm:buses'
            }
        }
    }
}
