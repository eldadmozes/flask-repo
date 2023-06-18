pipeline {
    agent any

    stages {
        stage('build image') {
            steps {
                sh "docker build -t flask-frontend:${params.flask_version} ."
            }
        }   
        stage('Check Kubernetes') {
            steps {
                sh 'kubectl get all --namespace flask-space'
            }
        }
        stage('Flask-deploy'){
            steps{
                sh 'kubectl apply -f flask-deployment.yaml'
            }
        }
    }
}