pipeline {
    agent any

    environment {
        AWS_ACCOUNT_ID = "219775392856"
        AWS_REGION = "eu-north-1"
        FRONTEND_REPO = "frontend"
        BACKEND_REPO = "backend"
        REGISTRY = "${AWS_ACCOUNT_ID}.dkr.ecr.${AWS_REGION}.amazonaws.com"
        DOCKER_BUILDKIT = "1"
    }

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'git@github.com:SUHEL782/MERN-Ecommerce.git'
            }
        }

        stage('Build Backend Image') {
            steps {
                sh 'docker build -t backend ./mern/Back-end-Integration'
            }
        }

        stage('Build Frontend Image') {
            steps {
                sh 'docker build -t frontend ./mern/front-end-integration'
            }
        }

        stage('Scan Images (Trivy)') {
            steps {
                sh '''
                trivy image --exit-code 1 --severity HIGH,CRITICAL backend
                trivy image --exit-code 1 --severity HIGH,CRITICAL frontend
                '''
            }
        }

        stage('Login to ECR') {
            steps {
                sh '''
                aws ecr get-login-password --region $AWS_REGION | \
                docker login --username AWS --password-stdin $REGISTRY
                '''
            }
        }

        stage('Tag Images') {
            steps {
                sh '''
                docker tag backend:latest $REGISTRY/$BACKEND_REPO:latest
                docker tag frontend:latest $REGISTRY/$FRONTEND_REPO:latest
                '''
            }
        }

        stage('Push Images to ECR') {
            steps {
                sh '''
                docker push $REGISTRY/$BACKEND_REPO:latest
                docker push $REGISTRY/$FRONTEND_REPO:latest
                '''
            }
        }
    }
}
