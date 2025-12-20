pipeline {
    agent any

    environment {
        IMAGE_NAME = "localhost:32000/igp_2025:${BUILD_NUMBER}"
    }

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/amizak/Igpsep25.git'
            }
        }

        stage('Compile') {
            steps {
                sh 'mvn compile'
            }
        }

        stage('Test & Package') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh '''
                cp target/ABCtechnologies-1.0.war .
                docker build -t igp_2025:${BUILD_NUMBER} .
                docker tag igp_2025:${BUILD_NUMBER} $IMAGE_NAME
                '''
            }
        }

        stage('Push Image to MicroK8s Registry') {
            steps {
                sh '''
                docker push $IMAGE_NAME
                '''
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh '''
                # Use the KUBECONFIG environment variable for kubectl
                sed -i "s|IMAGE_TAG|$IMAGE_NAME|g" deployment.yaml
                microk8s kubectl --kubeconfig=$KUBECONFIG apply -f deployment.yaml
                '''
            }
        }
    }
}
