pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/a4527/k3s-flask-cicd'
            }
        }

        stage('Build Flask1') {
            steps {
                sh 'docker build -f Dockerfile1 -t flask1:latest .'
            }
        }

        stage('Build Flask2') {
            steps {
                sh 'docker build -f Dockerfile2 -t flask2:latest .'
            }
        }

        stage('OCIR Login') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'ocir-cred', usernameVariable: 'OCIR_USER', passwordVariable: 'OCIR_PASS')]) {
                    sh '''
                        docker login yny.ocir.io -u "$OCIR_USER" -p "$OCIR_PASS"
                    '''
                }
            }
        }

        stage('Push Images') {
            steps {
                sh """
                docker tag flask1:latest yny.ocir.io/axvejxrm1ole/flask1:latest
                docker tag flask2:latest yny.ocir.io/axvejxrm1ole/flask2:latest

                docker push yny.ocir.io/axvejxrm1ole/flask1:latest
                docker push yny.ocir.io/axvejxrm1ole/flask2:latest
                """
            }
        }

        stage('Deploy to K8s') {
            steps {
                sh 'kubectl apply -f k8s/'
            }
        }
    }
}
