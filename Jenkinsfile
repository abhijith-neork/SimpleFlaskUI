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
                    withDockerRegistry(credentialsId: '39d4cf95-d261-457a-af94-42f4366d35da') {
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
