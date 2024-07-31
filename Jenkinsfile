pipeline {
    agent any

    stages {
        stage('Git Checkout') {
            steps {
                git 'https://github.com/abhijith-neork/SimpleFlaskUI.git'
            }
        }
        stage('Docker Build and Push') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'b4f77e8b-ae71-44cc-aada-345a670dbc41') {
                        sh "docker build -t abhijith99954/simpleflask ."
                        sh "docker tag abhijith99954/simpleflask:latest abhijith99954/simpleflask:latest"
                        sh "docker push abhijith99954/simpleflask:latest"
                    }
                }
            }
        }
        stage('Docker Run') {
            steps {
                sh "docker run -d -p 5000:5000 abhijith99954/simpleflask:latest"
            }
        }
    }
}
